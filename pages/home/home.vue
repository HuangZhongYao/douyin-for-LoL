<template>
	<view class="page">
		<!-- 顶部标题 -->
		<text class="title">推荐</text>

		<!-- 视频滑动区域 -->
		<swiper ref="cc" vertical class="s" id="videoc" @change="changefun" :current="videoIndex">
			<swiper-item  v-for="(video,index) in videoList">
				<view>
					<!-- 视频 -->
					<video @click="click()" :id="'video'+index" object-fit="cover" class="main" loop="true"
						:controls="false" :src="video.path"></video>
					
					<!-- 点赞图标 -->
					<image @click="like()" class="zan" :style="zanAnimation"
						:src="zan? '../../static/icon/zan-2.png':'../../static/icon/zan-1.png'"></image>
				</view>
			</swiper-item>
		</swiper>
		
		<!-- 暂停图标 -->
		<image v-show='pause' @click="click()" class="pause-icon" 
				src="../../static/icon/pause.png"></image>
		
	</view>
</template>

<script>
	
	export default {
		data() {
			return {
				videoList: [],
				videoIndex: 0,
				videoContext: null,
				pause: false,
				zan: false,
				zanAnimation: '',
				tips: '',
				queryPage: {
					pageNo: 1,
					pageSize: 5
				}
			}
		},
		onLoad() {
			
			// 进入页面加载数据
			this.loadData();
			// 判断是否需要自动播放视频
			this.isAutoPaly();
		},
		onShow() {
			// 回到判断是否需要自动播放视频
			this.isAutoPaly();
		},
		methods: {
			// 加载数据
			loadData() {
				let _this = this;
				// 请求数据
				uni.request({
					url: getApp().globalData.baseApi+"/resource/pageList",
					data: _this.queryPage,
					method: "POST",
					// 请求成功
					success(res) {
						_this.videoList = _this.videoList.concat(res.data.records);
					},
					// 请求失败
					fail() {

					}

				});
			},
			// 点赞
			like() {
				this.zan = !this.zan;
				// 添加点击动画效果
				this.zanAnimation = this.zan ? 'animation: scaleUp 0.2s linear forwards' :
					'animation: scaleDown 0.2s linear forwards';

				// 清除动画样式
				setTimeout(() => {
					this.zanAnimation = '';
				}, 200);
			},
			//滑动视频事件
			changefun(e) {
				console.log("changefun: ","videoIndex: ",this.videoIndex)
				let firstPage = this.videoIndex != 0 && ((this.videoIndex % 9) == 0);
				console.log("firstPage: ",firstPage)
				// 判断是否是第一页
				if (this.videoIndex != 0 && ((this.videoIndex % 3) == 0)) {
					firstPage = false;
					this.queryPage.pageNo++;
					console.log("videoIndex: ",this.videoIndex)
					this.loadData();
					
					console.log("videoList:",this.videoList)
					
				}

				//暂停其它视频
				for (let i = 0; i < this.videoList.length; i++) {
					uni.createVideoContext('video' + i).pause();
				}
				// 播放当前视频
				this.videoIndex = e.detail.current;
				this.videoContext = uni.createVideoContext('video' + this.videoIndex);
				this.videoContext.play();
			},
			// 视频点击事件
			click() {
				if (this.pause) {
					this.pause = false;
					this.play();
				} else {
					this.pause = true;
					this.pauseVideo();
				}
			},
	
			//播放
			play() {
				console.log("play  paus:",this.pause)
				this.videoContext.play();
				this.pause = false;

			},
			//暂停视频
			pauseVideo() {
				console.log("pauseVideo  paus:",this.pause)
				this.videoContext.pause();
				this.pause = true;
			},
			//是否自动播放视频
			isAutoPaly() {
				// 视频初始化
				this.videoContext = uni.createVideoContext('video' + this.videoIndex);
				// 如果不是用户暂停视频则自动播放
				if (this.pause == false) {
					this.videoContext.play();
					console.log("autoPaly")
				}
			}
		}
	}
</script>

<style>
	.title {
		width: 100%;
		position: absolute;
		z-index: 999;
		color: white;
		text-align: center;
		padding-top: 15px;

	}

	.s {
		height: 100%;
		width: 100%;
	}

	.page {
		height: 100%;
	}
	
	.pause-icon{
		    position: absolute;
		    z-index: 999;
		    position: absolute;
		    top: 49%;
		    left: 50%;
		    transform: translate(-50%, -50%);
		    width: 15%;
		    height: 8%;
		    animation-duration: 0.2s;
		    animation-fill-mode: forwards;
	}

	.zan {
		z-index: 999;
		position: absolute;
		top: 50%;
		left: 90%;
		transform: translate(-50%, -50%);
		width: 10%;
		height: 6%;
		animation-duration: 0.2s;
		animation-fill-mode: forwards;
	}

	.main {
		width: 100%;
		height: 100%;
		object-fit: cover;
		position: absolute;
	}

	@keyframes scaleUp {
		0% {
			transform: scale(1);
		}

		50% {
			transform: scale(1.5);
		}

		100% {
			transform: scale(1);
		}
	}

	@keyframes scaleDown {
		0% {
			transform: scale(1);
		}

		50% {
			transform: scale(0.5);
		}

		100% {
			transform: scale(1);
		}
	}
</style>
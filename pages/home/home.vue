<template>
	<view class="page">
		<text class="title">推荐</text>

		<swiper ref="cc" vertical class="s" id="videoc" @change="changefun">
			<swiper-item v-for="(video,index) in videoList">
				<view>
					<video @click="click()" :id="'video'+index" object-fit="cover" class="main" loop="true"
						:controls="false" :src="video"></video>
					<image @click="like()" class="zan" :style="zanAnimation"
						:src="zan? '../../static/icon/zan-2.png':'../../static/icon/zan-1.png'"></image>
				</view>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				videoList: [
					'../../static/video/lol-qinghuaci.mp4',
					'../../static/video/2016-1.mp4',
					'../../static/video/2016-2.mp4',
					'../../static/video/2017.mp4',
					'../../static/video/2022.mp4'
				],
				videoIndex: 0,
				videoContext: null,
				pause: false,
				zan: false,
				zanAnimation: ''
			}
		},
		onLoad() {
			this.isAutoPaly();
		},
		onShow() {
			this.isAutoPaly();
		},
		methods: {
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

				//暂停其它视频
				for (let i = 0; i < this.videoList.length; i++) {
					uni.createVideoContext('video' + i).pause();
				}
				// 播放当前视频
				this.videoIndex = e.detail.current;
				this.videoContext = uni.createVideoContext('video' + this.videoIndex);
				this.videoContext.play();
			},
			click() {
				if (this.pause) {
					this.play();
				} else {
					this.pauseVideo();
				}
			},
			//更改视频播放状态事件
			play() {
				console.log("play")
				this.videoContext.play();
				this.pause = false;

			},
			pauseVideo() {
				console.log("pause")
				this.videoContext.pause();
				this.pause = true;
			},
			isAutoPaly() {
				// 视频初始化
				this.videoContext = uni.createVideoContext('video' + this.videoIndex);
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

	.zan {
		position: absolute;
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
<template>
	<view class="page">
		<scroll-view scroll-y="true" class="scroll-Y">
		<view class="main">
			<view class="top">
				<view class="tag">
					<view class="tab-bar" @click="activiTabBar = 0" :class="activiTabBar == 0 ? 'activi-tab-bar':'' ">作品
					</view>
					<view class="tab-bar" @click="activiTabBar = 1" :class="activiTabBar == 1 ? 'activi-tab-bar':'' ">动态
					</view>
					<view class="tab-bar" @click="activiTabBar = 2" :class="activiTabBar == 2 ? 'activi-tab-bar':'' ">喜欢
					</view>
				</view>
			</view>

			<view class="content">
				<swiper class="swiper" @change="swiperChage" :current="activiTabBar" circular="true">
					<swiper-item>
						<scroll-view scroll-y="true" class="scroll-Y">
							<image src="../../static/image/example/22.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/23.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/24.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/25.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/26.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/27.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/28.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/29.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/30.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/31.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/32.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/33.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/34.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/35.jpg" mode="aspectFill" class="swiper-item">
							</image>

						</scroll-view>
					</swiper-item>
					<swiper-item>
						<scroll-view scroll-y="true" class="scroll-Y">
							<image src="../../static/image/example/11.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/12.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/13.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/14.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/15.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/16.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/17.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/18.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/19.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/20.jpg" mode="aspectFill" class="swiper-item">
							</image>
							<image src="../../static/image/example/21.jpg" mode="aspectFill" class="swiper-item">
							</image>
						</scroll-view>
					</swiper-item>
					<swiper-item>
						<scroll-view scroll-y="true" class="scroll-Y">
							<image src="../../static/image/example/1.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/2.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/3.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/4.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/5.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/6.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/7.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/8.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/9.jpg" mode="aspectFill" class="swiper-item"></image>
							<image src="../../static/image/example/10.jpg" mode="aspectFill" class="swiper-item">
							</image>
						</scroll-view>
					</swiper-item>
				</swiper>
			</view>

		</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				activiTabBar: 0,
			}
		},
		methods: {
			swiperChage(event) {
				this.activiTabBar = event.detail.current;

			}
		}
	}
</script>

<style>
	.scroll-Y {
		height: 100%;
		width: 100%;
	}

	.swiper {
		height: 100%;
		text-align: center;
		width: 100%;
	}

	.swiper-item {
		background-color: aliceblue;
		margin: 1px;
		width: 32%;
		height: 40%;
		float: left;
		text-align: center;
	}

	.activi-tab-bar {
		border-bottom: 1px solid #D1BC68;
	}

	.tab-bar {
		width: 31%;
		margin: 1px;
		padding: 2px;
		text-align: center;
		float: left;
		color: #454751;

	}

	.tag {
		position: absolute;
		bottom: 0px;
		width: 100%;
	}

	.content {
		height: 57%;
		width: 100%;
		background-color: #0E111E;
		padding: 1px;
	}

	.top {
		padding: 2px;
		background-color: #0E111E;
		border-top-left-radius: 25px;
		border-top-right-radius: 25px;
		border-style: none;
		border-bottom-color: #D1BC68;
		height: 43%;
		position: relative;
	}

	.main {

		position: absolute;
		height: 79%;
		width: 100%;
		z-index: 999;
		top: 21%;
	}

	.page {
		background-image: url('../../static/image/me-background-image.jpg');
		height: 100%;
		z-index: -1;
	}
</style>
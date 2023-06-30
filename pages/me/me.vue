<template>
	<view class="page">
		<view class="main">
			<view class="top">
				
			</view>
			<view class="like">
				
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style>
	.like{
		height: 57%;
		background-color: #151822;
	}
	.top{
		background-color: #151822;
		border-top-left-radius: 25px;
		border-top-right-radius: 25px;
		border-style: none;
		border-bottom-color: #D1BC68;
		height: 43%;
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
<template>
	<view class="content">
		<!-- <view class="head" :style="{ paddingTop: paddingTopNum + 'px' }"> -->
		<!-- <view class="head"> -->
			<!-- 标题插槽 -->
<!-- 			<slot name="title">
				<view style="width: 90%;text-align: center;">早上好！张三先生</view>
				<image src="../../static/notice.png"></image>
			</slot> -->
		<!-- </view> -->
		<!-- 防止顶到刘海屏等 -->
		<view :style="`height: ${statusBarHeight}px;`" class="status-bar"></view>
		<uni-nav-bar shadow left-icon="left" right-icon="notification-filled" title="早上好！张三先生" background-color="#000" color="aquamarine" height="100rpx"/>
		<!-- <view style="height: 30px;"></view> -->
		<view class="uni-margin-wrap">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay= "autoplay" :interval="interval"
				:duration="duration">
				<swiper-item v-for="(item, index) in imgArr" :key="index">
					<image class="swiper-item" :src="item.img" mode=“widthFix”></image>
				</swiper-item>
			</swiper>
		</view>
		<view class="flex-c gongneng">
			<view class="flex-c" style="flex-direction: column;">
				<image src="../../static/notice.png"></image>
				<text style="color: gray;">功能1</text>
			</view>
			<view class="flex-c"  style="flex-direction: column;">
				<image src="../../static/notice.png"></image>
				<text style="color: gray;">功能2</text>
			</view>
			<view class="flex-c"  style="flex-direction: column;">
				<image src="../../static/notice.png"></image>
				<text style="color: gray;">功能3</text>
			</view>
			<view class="flex-c"  style="flex-direction: column;">
				<image src="../../static/notice.png"></image>
				<text style="color: gray;">功能4</text>
			</view>
			<view class="flex-c"  style="flex-direction: column;">
				<image src="../../static/notice.png"></image>
				<text style="color: gray;">功能5</text>
			</view>
		</view>
		<view class="function">
			<view class="flex-c gongneng2" style="flex-wrap: wrap;flex-direction: column;"  v-for="(item, index) in funcOneArr" :key="index" @click="funcBFn(item)">
				<view class="wrap flex-a"  style="flex-wrap: wrap;">
					<view style="border-radius: 20rpx;border-bottom-right-radius: 0rpx;width: 50rpx; height: 50rpx;"><image src="../../static/notice.png"></image></view>
					<view style="border-radius: 20rpx;border-bottom-left-radius: 0;width: 50rpx; height: 50rpx;"><image src="../../static/notice.png"></image></view>
					<view style="border-radius: 20rpx;border-top-right-radius: 0;width: 50rpx; height: 50rpx;"><image src="../../static/notice.png"></image></view>
					<view style="border-radius: 20rpx;border-top-left-radius: 0;width: 50rpx; height: 50rpx;"><image src="../../static/notice.png"></image></view>
				</view>
				<text style="color: gray;">{{item}}</text>
			</view>

			<view class="flex-c gongneng2" v-for="(item, index) in funcArr" :key="index+'1'" style="flex-direction: column;">
				<view style="background-color: bisque;border-radius: 20rpx;margin-top: 10rpx;height: 100rpx;width: 100rpx;">
					<image src="../../static/notice.png"></image>
				</view>
				<text style="color: gray;margin: 10rpx 0;">{{item}}</text>
			</view>
		</view>
		<zdy-tabbar />
		<uni-popup ref="popup" background-color="#fff">
			<view style="width: 680rpx;">
				<view class="flex-c" style="background-color: black;height: 80rpx;color: greenyellow;">
					功能B
				</view>
				<view class="" style="display: grid;grid-template-columns: repeat(4, 1fr);">
					<view v-for="(item, index) in 10" :key="index" class="content-pop flex-a-s" style="flex-wrap: wrap;box-sizing: border-box;">
						<view class="flex-c" style="flex-direction: column;margin: 30rpx 36rpx">
							<image src="../../static/logo.png" alt="" srcset="" style="width: 100rpx;height: 100rpx;">
							功能1
						</view>
					</view>
				</view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	
	// import zdyTabbar from "@/components/zdy-tabbar.vue"
	export default {
		// components: {
		// 	zdyTabbar
		// },
		data() {
			return {
				//状态栏高度
				statusBarHeight: uni.getSystemInfoSync().statusBarHeight,
				// 导航区高度
				paddingTopNum: uni.getSystemInfoSync().statusBarHeight + 7,
				// 内容区高度
				pageTopHeight: uni.getSystemInfoSync().statusBarHeight + 30 + 7,
				background: ['color1', 'color2', 'color3'],
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				isShow: false,
				funcOneArr: ['功能A', '功能B', '功能C', '功能D'],
				funcArr: ['功能E', '功能F', '功能G', '功能H', '功能I', '功能J'],
				imgArr: [
					{
						img: require('../../static/1.jpeg')
					},
					{
						img: require('../../static/2.jpeg')
					},
					{
						img: require('../../static/3.jpeg')
					},
					{
						img: require('../../static/4.jpeg')
					},
					{
						img: require('../../static/5.jpeg')
					}
				]
			}
		},
		methods: {
			changeIndicatorDots(e) {
				this.indicatorDots = !this.indicatorDots
			},
			funcBFn(item) {
				if(item==='功能B')this.$refs.popup.open()

			}
		}
	}
</script>

<style lang="less" scoped>
	.content {
		background-color: #dfe6e8;
	}
// uni-page-head .uni-page-head {
// 		height: 0vh!important;
// 		padding: 0!important;
// 	}
	/* 自定义导航栏 */
	.flex-c {
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.flex-a {
		display: flex;
		align-items: flex-start;
		justify-content: space-around;
	}
	.flex-a-s {
		display: flex;
		align-items: flex-start;
		justify-content: start;
	}
	.head {
		position: fixed;
		width: 100%;
		z-index: 999;
		// height: 30px;
		line-height: 8vh;
		color: aquamarine;
		font-size: 32rpx;
		/* 设置背景为透明色 */
		background-color: #282A3A;
		top: 0;
		left: 0;
		height: 8vh;
		display: flex;
		align-items: center;
		image {
			width: 10%;
			height: 6vh;
		}
	}
	.uni-margin-wrap {
		width: 690rpx;
		width: 100%;
	}
	.swiper {
		height: 300rpx;
	}
	.swiper-item {
		display: block;
		width: 100%;
		height: 300rpx;
		line-height: 300rpx;
		text-align: center;
	}
	.uni-bg-red {
		background-color: red;
	}
	.uni-bg-green {
		background-color: greenyellow;
	}
	.uni-bg-blue {
		background-color: skyblue;
	}
	.gongneng {
		background-color: #000;
		height: 90rpx;
		font-size: 22rpx;
		view {
			flex: 1;
			image {
				height: 50rpx;
				width: 50rpx;
			}
		}
	}
	.function {
		display: flex;
		flex-wrap: wrap;
		margin-top: 15rpx;
		background-color: #fff;
		.gongneng2 {
			
			padding: 5rpx 0;
			width: 187.5rpx;
			border-right: 1rpx solid #ecf2f4;
			border-bottom: 1rpx solid #ecf2f4;
			box-sizing: border-box;
			.wrap {
				width: 110rpx;
				height: 110rpx;
				margin: 8rpx 0;
				view {
					background-color: orange;
				}
				image {
					width: 50rpx!important;
					height: 50rpx!important;
				}
			}
			image {
				width: 100rpx;
				height: 100rpx;
			}
			&:nth-of-type(4n) {
				border-right: 0rpx
			}
		}
		
	}
</style>

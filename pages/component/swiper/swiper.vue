<template>
	<view>
		<page-head title="swiper,可滑动视图"></page-head>
		<view class="uni-margin-wrap">
			<!--	这个 Vue 模板定义了一个轮播图组件（`swiper`），
			包含三个轮播项（`swiper-item`）。
			每个轮播项包含一个 `view` 元素，分别显示红色、绿色和蓝色背景，
			并显示文本 "A"、"B" 和 "C"。
			轮播图支持循环播放、指示点、自动播放、间隔时间和动画时长等属性。		-->
			<!-- 循环轮播组件，设置轮播图循环播放、指示点、自动播放等属性 -->
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
			    <!-- 轮播项 1 -->
			    <swiper-item>
			        <!-- 轮播图的第一项，带有红色背景 -->
			        <view class="swiper-item uni-bg-red">A</view>
			    </swiper-item>
			    <!-- 轮播项 2 -->
			    <swiper-item>
			        <!-- 轮播图的第二项，带有绿色背景 -->
			        <view class="swiper-item uni-bg-green">B</view>
			    </swiper-item>
			    <!-- 轮播项 3 -->
			    <swiper-item>
			        <!-- 轮播图的第三项，带有蓝色背景 -->
			        <view class="swiper-item uni-bg-blue">C</view>
			    </swiper-item>
			</swiper>
		</view>

		<view class="swiper-list">
			<view class="uni-list-cell uni-list-cell-pd">
				<view class="uni-list-cell-db">指示点</view>
				<switch :checked="indicatorDots" @change="changeIndicatorDots"/>
			</view>
			<view class="uni-list-cell uni-list-cell-pd">
				<view class="uni-list-cell-db">自动播放</view>
				<switch :checked="autoplay" @change="changeAutoplay"/>
			</view>
		</view>

		<view class="uni-padding-wrap">
			<view class="uni-common-mt">
				<text>幻灯片切换时长(ms)</text>
				<text class="info">{{ duration }}</text>
			</view>
			<slider @change="durationChange" :value="duration" min="500" max="2000"/>
			<view class="uni-common-mt">
				<text>自动播放间隔时长(ms)</text>
				<text class="info">{{ interval }}</text>
			</view>
			<slider @change="intervalChange" :value="interval" min="2000" max="10000"/>
		</view>
	</view>
</template>
<script>
export default {
	data() {
		return {
			background: ['color1', 'color2', 'color3'],
			indicatorDots: true,
			autoplay: true,
			interval: 2000,
			duration: 500
		}
	},
	methods: {
		changeIndicatorDots(e) {
			this.indicatorDots = !this.indicatorDots
		},
		changeAutoplay(e) {
			this.autoplay = !this.autoplay
		},
		intervalChange(e) {
			this.interval = e.detail.value
		},
		durationChange(e) {
			this.duration = e.detail.value
		}
	}
}
</script>

<style>
.uni-margin-wrap {
	width: 690rpx;
	width: 100%;;
}

.swiper {
	height: 300rpx;
}

.swiper-item {
	display: block;
	height: 300rpx;
	line-height: 300rpx;
	text-align: center;
}

.swiper-list {
	margin-top: 40rpx;
	margin-bottom: 0;
}

.uni-common-mt {
	margin-top: 60rpx;
	position: relative;
}

.info {
	position: absolute;
	right: 20rpx;
}

.uni-padding-wrap {
	width: 550rpx;
	padding: 0 100rpx;
}
</style>

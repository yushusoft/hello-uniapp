<template>
	<view>
		<page-head title="scroll-view,区域滚动视图"></page-head>
		<view class="uni-padding-wrap uni-common-mt">
			<view class="uni-title uni-common-mt">
				Vertical Scroll
				<text>\n纵向滚动</text>
			</view>
			<view>
				<!--该 Vue 模板定义了一个可滚动的视图组件 `<scroll-view>`，并绑定了以下功能：

				- `:scroll-top="scrollTop"`：设置滚动条的位置。
				- `scroll-y="true"`：允许垂直滚动。
				- `@scrolltoupper="upper"`：当滚动到顶部时触发 `upper` 方法。
				- `@scrolltolower="lower"`：当滚动到底部时触发 `lower` 方法。
				- `@scroll="scroll"`：在滚动过程中触发 `scroll` 方法。

				内部包含三个固定样式的子视图组件，分别显示 A、B、C。				-->
				<scroll-view :scroll-top="scrollTop" scroll-y="true"
							 class="scroll-Y" @scrolltoupper="upper"
							 @scrolltolower="lower"
							 @scroll="scroll">
					<view id="demo1" class="scroll-view-item uni-bg-red">A</view>
					<view id="demo2" class="scroll-view-item uni-bg-green">B</view>
					<view id="demo3" class="scroll-view-item uni-bg-blue">C</view>
				</scroll-view>
			</view>
			<view @tap="goTop" class="uni-link uni-center uni-common-mt">
				点击这里返回顶部
			</view>

			<view class="uni-title uni-common-mt">
				Horizontal Scroll
				<text>\n横向滚动</text>
			</view>
			<view>
				<scroll-view class="scroll-view_H" scroll-x="true" @scroll="scroll" scroll-left="120">
					<view id="demo1" class="scroll-view-item_H uni-bg-red">A</view>
					<view id="demo2" class="scroll-view-item_H uni-bg-green">B</view>
					<view id="demo3" class="scroll-view-item_H uni-bg-blue">C</view>
				</scroll-view>
			</view>
			<view class="uni-common-pb"></view>
		</view>
	</view>
</template>
<script>
export default {
	data() {
		return {
			scrollTop: 0,
			old: {
				scrollTop: 0
			}
		}
	},
	methods: {
		upper: function (e) {
			console.log(e)
		},
		lower: function (e) {
			console.log(e)
		},
		scroll: function (e) {
			console.log(e)
			this.old.scrollTop = e.detail.scrollTop
		},
		goTop: function (e) {
			/*
			*`goTop` 函数的功能是将页面滚动到顶部，并显示一个提示信息。

1. **同步滚动位置**：`this.scrollTop = this.old.scrollTop` 将当前滚动位置同步到 `this.scrollTop`，解决视图层不同步的问题。
2. **异步设置滚动位置**：使用 `this.$nextTick` 确保 DOM 更新后，将 `scrollTop` 设置为 0，实现滚动到顶部。
3. **显示提示信息**：使用 `uni.showToast` 显示一条消息，提示用户 `scrollTop` 已被修改为 0。
			*
			*
			*
			* */
			debugger;
			// 解决view层不同步的问题
			this.scrollTop = this.old.scrollTop
			this.$nextTick(function () {
				this.scrollTop = 0
			});
			uni.showToast({
				icon: "none",
				title: "纵向滚动 scrollTop 值已被修改为 0"
			})
		}
	}
}
</script>

<style>
.scroll-Y {
	height: 300rpx;
}

.scroll-view_H {
	white-space: nowrap;
	width: 100%;
}

.scroll-view-item {
	height: 300rpx;
	line-height: 300rpx;
	text-align: center;
	font-size: 36rpx;
}

.scroll-view-item_H {
	display: inline-block;
	width: 100%;
	height: 300rpx;
	line-height: 300rpx;
	text-align: center;
	font-size: 36rpx;
}
</style>

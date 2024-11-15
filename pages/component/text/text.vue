<template>
	<view>
		<page-head :title="title"></page-head>
		<view class="uni-padding-wrap uni-common-mt">
			<view class="text-box" scroll-y="true">
				<text>{{ text }}</text>
			</view>
			<view class="uni-btn-v">
				<button type="primary" :disabled="!canAdd" @click="add">add line</button>
				<button type="warn" :disabled="!canRemove" @click="remove">remove line</button>
			</view>
		</view>
	</view>
</template>
<script>
export default {
	data() {
		return {
			title: 'text',
			texts: [
				'HBuilder，400万开发者选择的IDE',
				'MUI，轻巧、漂亮的前端开源框架',
				'wap2app，M站快速转换原生体验的App',
				'5+Runtime，为HTML5插上原生的翅膀',
				'HBuilderX，轻巧、极速，极客编辑器',
				'uni-app，终极跨平台方案',
				'HBuilder，400万开发者选择的IDE',
				'MUI，轻巧、漂亮的前端开源框架',
				'wap2app，M站快速转换原生体验的App',
				'5+Runtime，为HTML5插上原生的翅膀',
				'HBuilderX，轻巧、极速，极客编辑器',
				'uni-app，终极跨平台方案',
				'......'
			],
			text: '',
			canAdd: true,
			canRemove: false,
			extraLine: []
		}
	},
	methods: {
		/**
		 * 添加文本行到extraLine数组中
		 * 此函数在用户界面中可能被调用，以处理添加文本行的操作
		 * 它根据当前行数从预定义的texts数组中选择文本，并更新界面显示的文本
		 * 同时，它会根据extraLine数组的长度来决定是否可以继续添加或删除行
		 *
		 * @param {Event} e - 可能是触发此函数的DOM事件对象
		 */
		add: function (e) {
			// 将texts数组中的下一个文本添加到extraLine数组中
			// 获取当前 extraLine 数组的长度
			const currentLength = this.extraLine.length;

			// 计算当前长度对 12 取模的结果，得到一个 0 到 11 之间的索引值
			const index = currentLength % 12;

			// 从 texts 数组中获取对应索引位置的文本
			const newText = this.texts[index];

// 将获取到的新文本添加到 extraLine 数组的末尾
			this.extraLine.push(newText);


			// 更新当前显示的文本，将其设置为extraLine数组中所有元素的换行符连接的结果
			this.text = this.extraLine.join('\n');

			// 更新canAdd属性，如果extraLine数组的长度小于12，则设置为true，表示可以继续添加行
			this.canAdd = this.extraLine.length < 12;

			// 更新canRemove属性，如果extraLine数组的长度大于0，则设置为true，表示可以删除行
			this.canRemove = this.extraLine.length > 0;
		},
		remove: function (e) {
			if (this.extraLine.length > 0) {
				this.extraLine.pop();
				this.text = this.extraLine.join('\n');
				this.canAdd = this.extraLine.length < 12;
				this.canRemove = this.extraLine.length > 0;
			}
		}
	}
}
</script>

<style>
.text-box {
	margin-bottom: 40rpx;
	padding: 40rpx 0;
	display: flex;
	min-height: 300rpx;
	background-color: #FFFFFF;
	justify-content: center;
	align-items: center;
	text-align: center;
	font-size: 30rpx;
	color: #353535;
	line-height: 1.8;
}
</style>

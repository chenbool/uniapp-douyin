<template>
	<view>
		<view class="list grid col-3 align-center justify-center">
			<block v-for="(item, index) in dataList" :key="index">
				<view class="video">
					<image :src="item.cover_url"></image>
				</view>
			</block>
		</view>
	</view>
</template>

<script>
export default {
	props: {
		dataList: {}
	},
	data() {
		return {};
	}
};
</script>

<style>
.list {
	display: flex;
	justify-content:space-between;
	flex-wrap: wrap;
	padding-bottom: 100rpx;
	padding: 5px;
	background: #161922;
	box-sizing: border-box;
}
.video{
	min-height: 400upx;
}
</style>

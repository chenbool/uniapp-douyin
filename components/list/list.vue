<template>
	<view>
		<view class="list">
			<block v-for="(item, index) in dataList" :key="index">
				<navigator class="video" :src="`/pages/video/video?video_id=${item.video_id}`"><image :src="item.cover_url"></image></navigator>
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
navigator {
	width: 50%;
	height: 90vw;
	padding: 5px;
	box-sizing: border-box;
	overflow: hidden;
}
navigator image{
	width: 100%;
	height: 100%;
	min-height: 390upx;
	border-radius: 10rpx;
}
</style>

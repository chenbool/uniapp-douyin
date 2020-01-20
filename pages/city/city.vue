<template>
	<view class="page" >
		<cu-custom bgColor="bg-black" :isBack="false">
			<block slot="backText">返回</block>
			<block slot="content">同城</block>
		</cu-custom>
		
		<view class="cu-item arrow bg-black padding soild-top">
			<view class="content">
				<text class="cuIcon-locationfill text-grey padding-right"></text>
				<text class="text-grey">自动定位: 临沂</text>
				<text class="cuIcon-right text-grey" style="float: right;"></text>
			</view>
		</view>
		
		<video-list :dataList="videoList"></video-list>
	</view>
</template>

<script>
import videoList from '@/components/list/list.vue';
export default {
	components: {
		videoList
	},
	data() {
		return {
			videoList: []
		};
	},
	onLoad() {
		this.getVideoList();
	},
	onPullDownRefresh() {
		console.log('refresh');
		this.getVideoList(true);
		uni.stopPullDownRefresh();
	},
	methods: {
		getVideoList() {
			uni.request({
				url: 'http://api.52170.xin/video?page_size=20',
				dataType: 'json',
				success: res => {
					console.log(res);
					for (let item of res.data.data.list) {
						this.videoList.push({
							video_id: item.video_id,
							nickname: item.nickname,
							video_describe: item.video_describe,
							cover_url: item.cover_url,
							video_url: item.video_url,
							dianzan: item.dianzan,
							pinglun: item.pinglun,
							zhuanfa: item.zhuanfa,
							flag: false,
							check: false
						});
					}
				}
			});
		}
		
		
	}
};
</script>
<style>
.page {
	background-color: #161922;
}
.soild-top{
	border-top: 1px solid #555555;
}
</style>

<template>
	<view class="index">

		<index-header bgColor="bg-index-header" @headerSwitch="headerSwitch"/>

		<!-- 视频组件 -->
		<cu-video class="video" :video_list="videoList"/>

	</view>
</template>

<script>
	import indexHeader from '@/components/index-header.vue';
	import cuVideo from '@/components/cu-video.vue';
	export default {
		components: {
			indexHeader,
			cuVideo
		},
		data() {
			return {
				title: 'Hello',
				videoList:[]
			}
		},
		onLoad() {
			this.getVideoList();
		},
		onShow() {
			console.log('界面显示')
		},
		methods: {

			getVideoList(refresh) {
				uni.request({
					url: 'https://api.52170.xin/video',
					dataType: 'json',
					success: res => {
						console.log(res.data.data.list);
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
								is_dianzan: item.is_dianzan,
								flag: false
							});
						}

					}
				});
			},
			// 顶部切换
			headerSwitch(val){
				// console.log(val);
				this.getVideoList();
			}
			
			
			
			
		}
		
	}
</script>

<style lang="less">
	.index {
		display: flex;
		flex-direction: column;
		/* align-items: center; */
		justify-content: center;
		background-color: #333333;
		height: 100vh;
	}
	.tabbar{
		.action{
			.plus{
				image{
					width: 100upx;
					height: 60upx;
				}
			}
		}
	}
</style>

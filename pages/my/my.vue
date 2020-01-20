<template>
	<view class="my">
		<cu-custom bgColor="bg-black" :isBack="false">
			<block slot="backText">返回</block>
			<block slot="content">我的</block>
		</cu-custom>
		
		<view class="banner"></view>
		
		<view class="user-info grid col-2 align-center justify-center">
			<view class="header align-center justify-center">
				<image src="../../static/logo.png" class="round" mode="widthFix"></image>
			</view>
			<view class="right">
				<text class="btn">编辑资料</text>
				<text class="btn">+</text>
			</view>
		</view>
		
		<!-- username -->
		<view class="grid user-detail col-2 align-center justify-center">
			<view class="left flex justify-center">
				<view class="">
					<text class="text-white text-xl"> 布尔 </text>
				</view>
				<view class="number">
					<text class="text-white"> 抖音号：100001 </text>
				</view>
				<view class="text-gray">
					<text class=""> + 添加联系方式 </text>
				</view>
			</view>
			<view class="right">

			</view>
		</view>
		
		<!-- 签名 -->
		<view class="qianming">
			<text class="text-white">个人签名</text>
		</view>
		
		<!--  -->
		<view class="grid col-3 align-center justify-center text-white">
			<view class="flex align-center justify-center">
				<text class="text-xl text-bold margin-right-xs">5000</text>
				<text class="text-gray">获赞</text>
			</view>
			<view class="flex align-center justify-center">
				<text class="text-xl text-bold margin-right-xs">5000</text>
				<text class="text-gray">关注</text>
			</view>
			<view class="flex align-center justify-center">
				<text class="text-xl text-bold margin-right-xs">5000</text>
				<text class="text-gray">粉丝</text>
			</view>
		</view>
		
		<!-- 广告 -->
		<view class="adv flex align-center justify-center">
			<image src="../../static/adv.png" mode="widthFix"></image>
		</view>
		
		<!-- tab -->
		<scroll-view scroll-x class="bg-black nav text-center">
			<view class="cu-item text-gray" :class="index==TabCur?'text-white cur':''" v-for="(item,index) in tabList" :key="index" @tap="tabSelect" :data-id="index">
				{{item.name}} 
				<text class="text-gray margin-left-xs">{{item.number}}</text> 
			</view>
		</scroll-view>
		
		<!-- list -->
		<video-list :dataList="videoList"></video-list>
		
	</view>
</template>

<script>
	import videoList from '@/components/my/list.vue';
	export default {
		components: {
			videoList
		},
		data() {
			return {
				TabCur: 0,
				scrollLeft: 0,
				tabList:[
					{
						name:'作品',
						number: 114
					},
					{
						name:'喜欢',
						number: 99
					},
				],
				videoList: []
			};
		},
		onLoad() {
			this.getVideoList();
		},
		methods:{
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60;
				this.getVideoList();
			},
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
	}
</script>

<style lang="less">
.my{
	background-color: #161823;
	height: 100vh;
	width: 100vw;
}
.banner{
	background-image: url(https://ossweb-img.qq.com/images/lol/web201310/skin/big39000.jpg);
	width: 100vw;
	min-height: 200upx;
	background-size: cover;
}
.user-info{
	.header{
		text-align: center;
		padding: 10upx 0;
		image{
			width: 150upx;
			height: 150upx;
		}
	}
	.right{
		.btn{
			background-color: rgba(57,58,68,0.5);
			color: #FFFFFF;
			padding: 15upx 30upx;
			margin: 0 8upx;
			border: 1px solid rgba(217,210,194,0.3);
		}
	}
}

.user-detail{
	border-bottom: 1px solid rgba(217,210,194,0.2);
	padding: 10upx 0;
	.left{
		flex-direction: column;
		text-align: left;
		padding-left: 80upx;
		// margin-left: 30upx;
		.number{
			margin: 10upx 0;
		}
	}
}

.qianming{
	padding: 20upx;
	padding-left: 80upx;
}

.adv{
	padding: 20upx;
}
</style>

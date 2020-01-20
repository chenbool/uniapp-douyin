<template>
	<view class="msg">
		<cu-custom bgColor="bg-black" :isBack="false">
			<block slot="backText">返回</block>
			<block slot="content">消息</block>
		</cu-custom>
		
		<!-- tools -->
		<view class="cu-list grid col-4 tools align-center justify-center">
				<view class="flex align-center justify-center">
					<image src="../../static/msg/fans.png" mode="widthFix"></image>
					<text>粉丝</text>
				</view>
				<view class="flex align-center justify-center">
					<image src="../../static/msg/zan.png" mode="widthFix"></image>
					<text>赞</text>
				</view>
				<view class="flex align-center justify-center">
					<image src="../../static/msg/at.png" mode="widthFix"></image>
					<text>@我的</text>
				</view>
				<view class="flex align-center justify-center">
					<image src="../../static/msg/comment.png" mode="widthFix"></image>
					<text>评论</text>
				</view>
		</view>
		
		<!-- list -->
			<view class="cu-list menu-avatar msg-list">
				<view class="cu-item">
					<view class="cu-avatar round lg" style="background-image:url(https://ossweb-img.qq.com/images/lol/web201310/skin/big10001.jpg);"></view>
					<view class="content">
						<view class="text-grey">凯尔</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">
								<text class="cuIcon-infofill text-red  margin-right-xs"></text>
								我已天理为凭，踏入这片荒芜，不再受凡人的枷锁遏制。我已天理为凭，踏入这片荒芜，不再受凡人的枷锁遏制。
							</view> </view>
					</view>
					<view class="action">
						<view class="text-grey text-xs">22:20</view>
						<view class="cu-tag round bg-grey sm">5</view>
					</view>
				</view>
				<view class="cu-item">
					<view class="cu-avatar round lg" style="background-image:url(https://ossweb-img.qq.com/images/lol/img/champion/Taric.png);">
						<view class="cu-tag badge">99+</view>
					</view>
					<view class="content">
						<view class="text-grey">
							<view class="text-cut">瓦洛兰之盾-塔里克</view>
							<view class="cu-tag round bg-orange sm">战士</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">
								塔里克是保护者星灵，用超乎寻常的力量守护着符文之地的生命、仁爱以及万物之美。塔里克由于渎职而被放逐，离开了祖国德玛西亚，前去攀登巨神峰寻找救赎，但他找到的却是来自星界的更高层的召唤。现在的塔里克与古代巨神族的神力相融合，以瓦洛兰之盾的身份，永不疲倦地警惕着阴险狡诈的虚空腐化之力。
							</view>
						</view>
					</view>
					<view class="action">
						<view class="text-grey text-xs">22:20</view>
						<view class="cuIcon-notice_forbid_fill text-gray"></view>
					</view>
				</view>
				<view class="cu-item ">
					<view class="cu-avatar radius lg" style="background-image:url(https://ossweb-img.qq.com/images/lol/img/champion/Morgana.png);"></view>
					<view class="content">
						<view class="text-pink"><view class="text-cut">莫甘娜</view></view>
						<view class="text-gray text-sm flex"> <view class="text-cut">凯尔，你被自己的光芒变的盲目！</view></view>
					</view>
					<view class="action">
						<view class="text-grey text-xs">22:20</view>
						<view class="cu-tag round bg-red sm">5</view>
					</view>
				</view>
				<view class="cu-item grayscale">
					<view class="cu-avatar radius lg" style="background-image:url(https://ossweb-img.qq.com/images/lol/web201310/skin/big81007.jpg);"></view>
					<view class="content">
						<view><view class="text-cut">伊泽瑞尔</view>
							<view class="cu-tag round bg-orange sm">断开连接...</view>
						</view>
						<view class="text-gray text-sm flex"> <view class="text-cut"> 等我回来一个打十个</view></view>
					</view>
					<view class="action">
						<view class="text-grey text-xs">22:20</view>
						<view class="cu-tag round bg-red sm">5</view>
					</view>
				</view>
				<view class="cu-item cur">
					<view class="cu-avatar radius lg" style="background-image:url(https://ossweb-img.qq.com/images/lol/web201310/skin/big81020.jpg);">
						<view class="cu-tag badge"></view>
					</view>
					<view class="content">
						<view>
							<view class="text-cut">瓦罗兰大陆-睡衣守护者-新手保护营</view>
							<view class="cu-tag round bg-orange sm">6人</view>
						</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut"> 伊泽瑞尔：<text class="cuIcon-locationfill text-orange margin-right-xs"></text> 传送中...</view></view>
					</view>
					<view class="action">
						<view class="text-grey text-xs">22:20</view>
						<view class="cuIcon-notice_forbid_fill text-gray"></view>
					</view>
				</view>
			</view>	
		
		
		
		
		
		
		
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="less">
	
.msg{
	width: 100vw;
	height: 100vh;
	background-color: #161823;
}
.tools{
	view{
		display: flex;
		flex-direction: column;
	}
	image{
		width: 100upx;
		height: 100upx;
		display: flex;
	}
}
.cu-list.grid{
	background-color: #161823;
	padding: 30upx 0;
	color: #FFFFFF;
	border-bottom: 1px solid rgba(110,111,117,0.5);
}
.cu-list+.cu-list{
	margin-top: 0;
}
.cu-list.menu-avatar>.cu-item{
	background-color: #161823;
	border-color: rgba(110,111,117,0.5);
}
</style>

<template>
	<view class="index-header">
		<view class="cu-custom" :style="[{height:CustomBar + 'px'}]">
			<view class="cu-bar fixed" :style="style" :class="bgColor">
				
				<view class="action" @tap="SwitchTab(1)">
					<text class="cuIcon-playfill"></text>
				</view>
				
				<view class="content-1" :style="[{top:StatusBar + 'px'}]">
					<view class="action">
						<view class="item" 
						:class="SwitchCur == 1 ? 'selected' : null "
						@tap.stop="SwitchTab(1)">关注</view>
						<view class="item"
						 :class="SwitchCur == 2 ? 'selected' : null "
						 @tap.stop="SwitchTab(2)">
							<text>推荐</text>
						 </view>
					</view>
				</view>
				
				<view class="right" @tap="SwitchTab(2)">
					<text class="cuIcon-search"></text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				StatusBar: this.StatusBar,
				CustomBar: this.CustomBar,
				SwitchCur: 2
			};
		},
		name: 'index-header',
		computed: {
			style() {
				var StatusBar= this.StatusBar;
				var CustomBar= this.CustomBar;
				var bgImage = this.bgImage;
				var style = `height:${CustomBar}px;padding-top:${StatusBar}px;`;
				if (this.bgImage) {
					style = `${style}background-image:url(${bgImage});`;
				}
				return style
			}
		},
		props: {
			bgColor: {
				type: String,
				default: ''
			},
			isBack: {
				type: [Boolean, String],
				default: false
			}
		},
		methods: {
			SwitchTab(val) {
				this.SwitchCur = val;
				// console.log( this.SwitchCur );
				this.$emit('headerSwitch',val);
			}
		}
	}
</script>

<style lang="less">
.cu-custom{
	.bg-index-header{
		background-color: rgba(255,255,255,0);
	}
	.action{
		.cuIcon-playfill{
			background-color: rgba(255,255,255,0.5);
			border-radius: 50upx;
			padding: 18upx;
			color: #FFFFFF;
		}
	}
	
	.right{
		padding-right: 30upx;
		.cuIcon-search{
			background-color: rgba(255,255,255,0.5);
			border-radius: 50upx;
			padding: 18upx;
			color: #FFFFFF;
		}
	}
	.content-1{
		.action{
			border-radius: 80upx;
			background-color: rgba(255,255,255,0.2);
			.item{
				border-radius: 80upx;
				padding: 12upx 30upx;
				margin: 0 5upx;
				color: #FFFFFF;
			}
			.selected{
				background-color: rgba(255,255,255,0.5);
			}
		}
	}
}

</style>

<template>
	<view>
		
		<swiper class="swiper" autoplay="false" vertical="true" interval="990000" @change="changeVideo">
			<swiper-item v-for="(item,index) in video_list">

				<video
					:src="item.video_url"
					preload
					show-play-btn="true"
					controls="false"
					v
					loop="true"
					:id="`video_${item.video_id}`"
					objectFit="fill"
					:enable-progress-gesture="false"
					@click="clickVideo"
					ref="video_url"
					play-btn-position="center"
					class="video"
					:poster="item.cover_url"
					@timeupdate="timeupdate">
				</video>
				
				<cover-image 
				class="play" v-if="show_play" 
				@tap="videoPlay"
				src="/static/video/play_1.png"></cover-image>
				
				<cover-view class="cover-view-left">
					<text class="view-left-text">@{{ item.nickname }}</text>
					<view class="view-left-text-content">
						<text class="text-content-text">{{ item.video_describe }}</text>
					</view>
				</cover-view>
				
				<cover-view class="cover-view-right">
					<cover-image :src="item.cover_url"
					 class="avater img" 
					 @click.stop="tapAvater"></cover-image>
					
					<text class="right-follow">+</text>
					<cover-image 
					style="position:relative;top:-20upx;"
					:src="item.is_dianzan ? '/static/video/axc.png' : '/static/video/bed.png'" 
					class="img-left" @click.stop="tapLove"></cover-image>
					
					<text class="right-text">{{ item.dianzan }}</text>
					<cover-image src="/static/video/ay2.png" 
					style="height: 80upx;" class="img-left" @click.stop="tapMsg"></cover-image>
					
					<text class="right-text">{{ item.pinglun }}</text>
					<cover-image src="/static/video/b6p.png" 
					style="height: 76upx;" class="img-left" @click.stop="tapShare"></cover-image>
					
					<text class="right-text">{{ item.zhuanfa }}</text>
					<cover-image src="/static/video/changpian.png" class="musicIcon img">
					</cover-image>
					
					<cover-view class="progressBar" :animation="animationData" :style="`width:${barWidth}px`"></cover-view>
					
					
				</cover-view>





			</swiper-item>
		</swiper>

	</view>
</template>
<script>
let play = false;
export default {
	props: {
		video_list: {
			type: Array,
			default: {}
		}
	},
	data() {
		return {
			time: 0,
			barWidth:0,
			animationData: {},
			times:null,
			play: false,
			show_play:false,
			current_index: 0
		};
	},
	created() {
		setTimeout(()=>{
			play = true;
			this.videoPlay();
		},1000)
	},
	methods: {
		timeupdate(event) {
			let t_w = parseInt(this.width);
			this.duration = event.detail.duration;
			this.time = event.detail.currentTime;
			let width = (this.time / this.duration) * t_w;
			let w = 0;
		},
		clickVideo() {
			// console.log('单视频点击事件');
			this.videoPlay();
		},
		videoPlay() {
			let video_id = this.video_list[this.current_index].video_id;
			
			if (play) {
				console.log('播放视频',`video_${video_id}`);
				this.videoCtx = uni.createVideoContext(`video_${video_id}`, this);
				this.videoCtx.play();
				this.show_play = false;
				play = false;
			} else {
				console.log('暂停视频',`video_${video_id}`);
				this.videoCtx = uni.createVideoContext(`video_${video_id}`, this);
				this.videoCtx.pause();
				this.show_play = true;
				play = true;
			}
		},
		videoPause() {
			let video_id = this.video_list[this.current_index].video_id;
			this.videoCtx = uni.createVideoContext(`video_${video_id}`, this);
			this.videoCtx.pause();
			this.show_play = true;
			play = true;
		},
		changeVideo(e){
			
			// 暂停之前的视频
			this.videoPause();
			this.current_index = e.detail.current;
			console.log(e.detail.current);
			// 播放现在的视频
			this.videoPlay();
			
			// 判断是否第一条
			if( e.detail.current == 0 ){
				console.log('到顶了');
				return false;
			}
			
			// 判断是否最后一条
			if( e.detail.current == this.video_list.length-1 ){
				console.log('到底了');
				return false;
			}
			
		},
		tapMsg(e) {
			console.log(5, e);
		},
		tapShare(e) {
			console.log(6, e);
		},
		tapLove(e) {
			// item.is_dianzan
			this.video_list[this.current_index].is_dianzan = !this.video_list[this.current_index].is_dianzan;
			console.log(7, e);
		}
		
	},
	watch: {
		play(newVal, oldVal) {
			this.videoPlay();
		}
	}
};
</script>

<style>
.swiper{
	width: 100vw;
	height: 100vh;	
	position: fixed;
	top: 0;
	left: 0;
}
.video {
	width: 100%;
	height: 100%;
	position: relative;
}
.play{
	position: absolute;
	width: 20vw;
	height: 20vw;
	left: 40vw;
	top: 40vh;
	opacity: 0.5;
}
.progressBar {
	border-radius: 2upx;
	height: 4upx;
	background-color: #FF4500;
	z-index: 999999;
	position: absolute;
	bottom: 68rpx;
}

.cover-view-left {
	position: absolute;
	margin-left: 20upx;
	width: 580upx;
	bottom: 110upx;
	z-index: 9999;
	font-size: 14px;
	color: #ffffff;
}
.left-text {
	font-size: 14px;
	color: #ffffff;
}

.cover-view-right {
	position: absolute;
	bottom: 40px;
	right: 30upx;
	z-index: 9999;
	text-align: center;
}

.avater {
	border-radius: 50%;
	border-width: 2px;
	border-style: solid;
	border-color: #ffffff;
}

.img {
	height: 90upx;
	width: 90upx;
	margin-bottom: 110upx;
}

.img-left {
	width: 80upx;
	height: 66upx;
	padding-left: 4px;
}
.right-follow {
	position: absolute;
	z-index: 100;
	top: 75upx;
	left: 28upx;
	color: #ffffff;
	font-size: 16px;
	width: 34upx;
	height: 34upx;
	background-color: #f12f5b;
	text-align: center;
	line-height: 34upx;
	border-radius: 17upx;
}

.right-text {
	color: #ffffff;
	font-size: 11px;
	text-align: center;
	margin-bottom: 40upx;
}
.musicIcon {
	margin-top: 40upx;
}
@keyframes rotating {
	from {
		transform: rotate(0);
	}
	to {
		transform: rotate(360deg);
	}
}
.view-left-text-content {
	flex: 1;
}
.view-left-text {
	color: #ffffff;
	font-size: 18px;
	margin-bottom: 10upx;
	font-weight: bold;
}
.text-content-text {
	color: #ffffff;
	font-size: 16px;
	line-height: 50upx;
	height: 100upx;
	overflow: hidden;
}
</style>

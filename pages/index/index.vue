<template>
	<view class="content com">
		<!-- <uni-notice-bar style="margin-bottom: 0px;" show-icon="true" scrollable="true" single="true" text="[每日一言] 这是 NoticeBar 通告栏，这是 NoticeBar 通告栏，这是 NoticeBar 通告栏">
		</uni-notice-bar> -->
		<view class="uni-padding-wrap uni-common-mt" >
			<view class="flex-center">
				<video style="width: 96%;" id="myVideo" src="https://img.cdn.aliyun.dcloud.net.cn/guide/uniapp/%E7%AC%AC1%E8%AE%B2%EF%BC%88uni-app%E4%BA%A7%E5%93%81%E4%BB%8B%E7%BB%8D%EF%BC%89-%20DCloud%E5%AE%98%E6%96%B9%E8%A7%86%E9%A2%91%E6%95%99%E7%A8%8B@20181126.mp4"
				 @error="videoErrorCallback" :danmu-list="danmuList" enable-danmu danmu-btn controls poster="https://img-cdn-qiniu.dcloud.net.cn/uniapp/doc/poster.png"></video>
			</view>
			<!-- #ifndef MP-ALIPAY -->
			<view class="uni-list uni-common-mt">
				<view class="uni-list-cell flex-center" style="padding: 40upx 0;font-size: 34upx;">
					<span>弹幕内容 : </span>
					<input v-model="danmuValue" type="text" placeholder="在此处输入弹幕内容" style="margin-left: 10px;color: #fff !important;" />
				</view>
			</view>
			<button class="page-body-button" @click="sendDanmu" type="primary" style="width: 60%;background-color: #fff!important;color: #ff9b8a;font-size: 34upx;">发送弹幕</button>

			<!-- #endif -->
		</view>
		<view class="login-bg flex-center" style="margin-top: 20upx; height: auto;">
			<view class="login-card">
				<!-- todo 换为图片 -->
				<view class="login-head">事业~爱情~财富~健康</view>
				<view class="login-input login-margin-b">
					<input type="" placeholder="姓名" style="text-align: center;" />
				</view>
				<view class="uni-list">
					<view class="uni-list-cell" style="display: flex;flex-direction: row;justify-content: center;font-size: 28upx;">
						<view class="uni-list-cell-left">
							性别 :
						</view>
						<view class="uni-list-cell-db">
							<picker @change="bindPickerChange" :value="index" :range="array" range-key="name">
								<view class="uni-input">{{array[index].name}}</view>
							</picker>
						</view>
					</view>
				</view>
				<view class="login-input">
					<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
						<view class="uni-input" style="font-size: 28upx; text-align: center;padding: 20upx 0;">选择出生年月日 : {{date}}</view>
					</picker>
				</view>
				<view class="login-btn" style="margin-top: 40upx;">
					<button class="landing" type="primary">卜一卜</button>
				</view>
			</view>
		</view>


	</view>
</template>

<script>
	function getDate(type) {
		const date = new Date();

		let year = date.getFullYear();
		let month = date.getMonth() + 1;
		let day = date.getDate();

		if (type === 'start') {
			year = year - 60;
		} else if (type === 'end') {
			year = year + 2;
		}
		month = month > 9 ? month : '0' + month;;
		day = day > 9 ? day : '0' + day;

		return `${year}-${month}-${day}`;
	}
	import uniNoticeBar from "@/components/uni-notice-bar/uni-notice-bar.vue"
	export default {
		components: {
			uniNoticeBar
		},
		data() {
			return {
				title: 'Hello',
				date: getDate({
					format: true
				}),
				startDate: getDate('start'),
				endDate: getDate('end'),
				array: [{
					name: '男'
				}, {
					name: '女'
				}],
				index: 0,
				src: '',
				danmuList: [{
						text: '第 1s 出现的弹幕',
						color: '#ff0000',
						time: 1
					},
					{
						text: '第 3s 出现的弹幕',
						color: '#ff00ff',
						time: 3
					}
				],
				danmuValue: ''
			}
		},
		onLoad() {

		},
		onReady: function(res) {
			// #ifndef MP-ALIPAY
			this.videoContext = uni.createVideoContext('myVideo')
			// #endif
		},
		methods: {
			bindPickerChange: function(e) {
				console.log('picker发送选择改变，携带值为：' + e.target.value)
				this.index = e.target.value
			},
			go_forget() {
				uni.navigateTo({
					url: '../../pages/forget/forget'
				})
			},
			go_register() {
				uni.navigateTo({
					url: '../../pages/register/register'
				})
			},
			
			bindDateChange: function(e) {
				this.date = e.target.value
			},
			bindTimeChange: function(e) {
				this.time = e.target.value
			},
			sendDanmu: function() {
				this.videoContext.sendDanmu({
					text: this.danmuValue,
					color: this.getRandomColor()
				});
				this.danmuValue = '';
			},
			videoErrorCallback: function(e) {
				uni.showModal({
					content: e.target.errMsg,
					showCancel: false
				})
			},
			getRandomColor: function() {
				const rgb = []
				for (let i = 0; i < 3; ++i) {
					let color = Math.floor(Math.random() * 256).toString(16)
					color = color.length == 1 ? '0' + color : color
					rgb.push(color)
				}
				return '#' + rgb.join('')
			}

		}
	}
</script>
<style>
	@import url("../../static/common.css");
</style>
<style>
	.content {
		/* background: linear-gradient(#FF978D, #FFBB69); */
		padding: 20upx;
	}

	.landing {
		height: 84upx;
		line-height: 84upx;
		border-radius: 44upx;
		font-size: 32upx;
		background: linear-gradient(left, #FF978D, #FFBB69);
	}

	.login-btn {
		padding: 10upx 20upx;
		margin-top: 350upx;
	}

	.login-function {
		overflow: auto;
		padding: 20upx 20upx 30upx 20upx;
	}

	.login-forget {
		float: left;
		font-size: 26upx;
		color: #999;
	}

	.login-register {
		color: #666;
		float: right;
		font-size: 26upx;

	}

	.login-input input {
		background: #F2F5F6;
		font-size: 28upx;
		padding: 10upx 25upx;
		height: 62upx;
		line-height: 62upx;
		border-radius: 8upx;
	}

	.login-margin-b {
		margin-bottom: 25upx;
	}

	.login-input {
		padding: 10upx 20upx;
	}

	.login-head {
		font-size: 34upx;
		text-align: center;
		padding: 25upx 10upx 55upx 10upx;
	}

	.login-card {
		width: 80%;
		background: #fff;
		border-radius: 12upx;
		padding: 10upx 25upx;
		box-shadow: 0 6upx 18upx rgba(0, 0, 0, 0.12);
		position: relative;
		margin-top: 20upx;
	}

	.
	/* login-bg {
		height: 260upx;
		padding: 25upx;
		background: linear-gradient(#FF978D, #FFBB69);
	} */


	video {
		width: 690upx;
	}

	.flex-left {
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: center;
	}

	.flex-center {
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
</style>

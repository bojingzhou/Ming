<template>
	<view class="content">
		<uni-notice-bar style="margin-bottom: 0px;" show-icon="true" scrollable="true" single="true" text="[每日一言] 这是 NoticeBar 通告栏，这是 NoticeBar 通告栏，这是 NoticeBar 通告栏">
		</uni-notice-bar>
		<view class="login-bg">
			<view class="login-card">
				<view class="login-head">事业~爱情~财富~健康</view>
				<view class="login-input login-margin-b">
					<input type="" placeholder="姓名" style="text-align: center;" />
				</view>
				<view class="login-input login-margin-b" style="display: flex;flex-direction: row;justify-content: center;font-size: 28upx;">
					<view class="title">性别 : </view>
					<radio-group name="radio" style="margin-left: 10px;">
						<label>
							<radio value="boy" style="transform: scale(0.7);" />男
						</label>
						<label>
							<radio value="girl" style="transform: scale(0.7);" />女
						</label>
					</radio-group>
				</view>
				<view class="login-input">
					<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
						<view class="uni-input" style="font-size: 28upx; text-align: center;padding: 20upx 0;">选择出生年月日 : {{date}}</view>
					</picker>
				</view>
			</view>
		</view>
		<view class="login-btn">
			<button class="landing" type="primary">卜一卜</button>
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
			}
		},
		onLoad() {

		},
		methods: {
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
			bindPickerChange: function(e) {
				console.log('picker发送选择改变，携带值为：' + e.target.value)
				this.index = e.target.value
			},
			bindMultiPickerColumnChange: function(e) {
				console.log('修改的列为：' + e.detail.column + '，值为：' + e.detail.value)
				this.multiIndex[e.detail.column] = e.detail.value
				switch (e.detail.column) {
					case 0: //拖动第1列
						switch (this.multiIndex[0]) {
							case 0:
								this.multiArray[1] = ['中国', '日本']
								this.multiArray[2] = ['北京', '上海', '广州']
								break
							case 1:
								this.multiArray[1] = ['英国', '法国']
								this.multiArray[2] = ['伦敦', '曼彻斯特']
								break
						}
						this.multiIndex.splice(1, 1, 0)
						this.multiIndex.splice(2, 1, 0)
						break
					case 1: //拖动第2列
						switch (this.multiIndex[0]) { //判断第一列是什么
							case 0:
								switch (this.multiIndex[1]) {
									case 0:
										this.multiArray[2] = ['北京', '上海', '广州']
										break
									case 1:
										this.multiArray[2] = ['东京', '北海道']
										break
								}
								break
							case 1:
								switch (this.multiIndex[1]) {
									case 0:
										this.multiArray[2] = ['伦敦', '曼彻斯特']
										break
									case 1:
										this.multiArray[2] = ['巴黎', '马赛']
										break
								}
								break
						}
						this.multiIndex.splice(2, 1, 0)
						break
				}
				this.$forceUpdate()
			},
			bindDateChange: function(e) {
				this.date = e.target.value
			},
			bindTimeChange: function(e) {
				this.time = e.target.value
			}

		}
	}
</script>

<style>
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
		background: #fff;
		border-radius: 12upx;
		padding: 10upx 25upx;
		box-shadow: 0 6upx 18upx rgba(0, 0, 0, 0.12);
		position: relative;
		margin-top: 120upx;
	}

	.login-bg {
		height: 260upx;
		padding: 25upx;
		background: linear-gradient(#FF978D, #FFBB69);
	}
</style>

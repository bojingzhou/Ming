<template>
	<view>
		<view class="header">
			<view class="bg com">
				<view class="box" style="height: 120px;border-radius: 6px;">
					<view class="box-hd">
						<view class="avator" style="width: 60px;height: 60px;">
							<img src="../../static/user/face.jpg">
						</view>
						<view class="phone-number" style="margin: 10px 0 0 0;">18909XXXX67</view>
					</view>
					<view class="box-bd">
						<!-- <view class="item">
							<view class="icon" style="width: 24px;height: 24px;"><img src="../../static/user/message.png"></view>
							<view class="text">我的积分</view>
						</view> -->
						<view class="item">
							<view class="icon" style="width: 24px;height: 24px;"><img src="../../static/user/favorite.png"></view>
							<view class="text">我的点赞</view>
						</view>
						<!-- <view class="item">
							<view class="icon" style="width: 24px;height: 24px;"><img src="../../static/user/service.png"></view>
							<view class="text">我的客服</view>
						</view> -->
					</view>
				</view>
			</view>
		</view>
		<view class="list-content">
			<view class="list">
				<view class="li noborder">
					<view class="icon">
						<img src="../../static/user/card.png">
					</view>
					<view class="text">我的许愿</view>
					<img class="to" src="../../static/user/to.png">
				</view>
			</view>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {};
		},
		onLoad() {},
		methods: {
			changeSkin() {
				uni.navigateTo({
					url: '../skin-change/skin-change'
				});
			},
		}
	}
</script>
<style>
	@import url("../../static/common.css");
</style>
<style lang="scss">
	page {
		background-color: #f1f1f1;
		font-size: 30upx;
	}

	.header {
		background: #fff;
		height: 290upx;
		padding-bottom: 110upx;

		.bg {
			width: 100%;
			height: 200upx;
			padding-top: 100upx;
			background-color: #4191ea;
		/* background: linear-gradient(#FF978D, #FFBB69); */

		}
	}

	.box {
		width: 650upx;
		height: 280upx;
		border-radius: 20upx;
		margin: 0 auto;
		background: #fff;
		box-shadow: 0 5upx 20upx 0upx rgba(0, 0, 150, .2);

		.box-hd {
			display: flex;
			flex-wrap: wrap;
			flex-direction: row;
			justify-content: center;

			.avator {
				width: 160upx;
				height: 160upx;
				background: #fff;
				border: 5upx solid #fff;
				border-radius: 50%;
				margin-top: -80upx;
				overflow: hidden;

				img {
					width: 100%;
					height: 100%;
				}
			}

			.phone-number {
				width: 100%;
				text-align: center;
			}
		}

		.box-bd {
			display: flex;
			flex-wrap: nowrap;
			flex-direction: row;
			justify-content: center;

			.item {
				flex: 1 1 auto;
				display: flex;
				flex-wrap: wrap;
				flex-direction: row;
				justify-content: center;
				border-right: 1px solid #f1f1f1;
				margin: 15upx 0;

				&:last-child {
					border: none;
				}

				.icon {
					width: 60upx;
					height: 60upx;

					img {
						width: 100%;
						height: 100%;
					}
				}

				.text {
					width: 100%;
					text-align: center;
					margin-top: 10upx;
				}
			}
		}
	}

	.list-content {
		background: #fff;
	}

	.list {
		width: 100%;
		border-bottom: 15upx solid #f1f1f1;
		background: #fff;

		&:last-child {
			border: none;
		}

		.li {
			width: 92%;
			height: 100upx;
			padding: 0 4%;
			border-bottom: 1px solid rgb(243, 243, 243);
			display: flex;
			align-items: center;

			&.noborder {
				border-bottom: 0
			}

			.icon {
				flex-shrink: 0;
				width: 50upx;
				height: 50upx;

				image {
					width: 50upx;
					height: 50upx;
				}
			}

			.text {
				padding-left: 20upx;
				width: 100%;
				color: #666;
			}

			.to {
				flex-shrink: 0;
				width: 40upx;
				height: 40upx;
			}
		}
	}

	.icon {
		width: 22px !important;
		height: 22px !important;
	}

	.icon img {
		width: 100%;
		height: 100%
	}
</style>

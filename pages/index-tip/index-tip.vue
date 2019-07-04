<template>
	<view class="m-store-store">
		<view class="m-store-banner">
			<view class="m-content">
				<view class="m-message">
					<view class="m-img">
					</view>
					<view class="m-body">
						<view class="m-title">
							蔬菜001号(中关村店)
						</view>
						<view class="m-text">
							公告：全场绿色蔬菜活动特价8.5折进行中
						</view>
						<view class="m-time">
							营业：07:00-23:00
						</view>
					</view>
					<view class="m-phone">
						<image style="width: 40upx;height:40upx;" src="../../static/img/icon/shop_icon_phone.png" mode="aspectFit"></image>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>
<script>
	
	export default {
		components:{
	
		},
		data() {
			return {
	
			}
		},
		methods:{
			//分类切换显示
	
		},
		watch:{
	
		},
		onLoad() {
	  
		}
		
	}
</script>
<style lang="scss">
	
	@keyframes showPopup {
			0% {
				opacity: 0;
			}
			100% {
				opacity: 1;
			}
		}
		@keyframes hidePopup {
			0% {
				opacity: 1;
			}
			100% {
				opacity: 0;
			}
		}
		@keyframes showLayer {
			0% {
				transform: translateY(0);
			}
			100% {
				transform: translateY(-100%);
			}
		}
		@keyframes hideLayer {
			0% {
				transform: translateY(-100%);
			}
			100% {
				transform: translateY(0);
			}
		}
	.m-store-banner{
		min-height: 270upx;
		position: relative;
		padding-top: 20upx;
		background:#eee;
		// background:url("../../static/img/storebanner.png");
		background-size: 100% 200upx;
		background-repeat: no-repeat;
		.m-content{
			width: 690upx;
			position: relative;
			bottom: 10upx;
			left: 30upx;
			right: 30upx;
			margin-top: 30upx;
			background:#fff;
			border-radius: 15upx;
			box-shadow: 0upx 5upx 20upx rgba(0,0,0,0.1);
			z-index: 100;
			.m-message{
				padding:20upx;
				display: flex;
				flex-direction: row;
				justify-content: space-between;
				align-items: flex-end;
				.m-img{
					flex:0 0 135upx;
					height: 135upx;
					// background:url("../../static/img/storebanner.png");
				}
				.m-body{
					flex: 1;
					// padding: 20upx;
					padding-left: 10upx;
					padding-bottom: 0;
					.m-title{
						font-size: 32upx;
						color:#333333
					}
					.m-text{
						font-size: 20upx;
						color:#999999;
						line-height: 38upx;
						margin-top: 10upx;
					}
					.m-time{
						font-size: 20upx;
						color:#999999;
						margin-top: 10upx;
					}
				}
				.m-phone{
					flex:0 0 40upx;
					text-align: right
				}
			}
		}
	}
	.popup {
		position: fixed;
		top: 0;
		width: 100%;
		height: 100%;
		z-index: 300;
		display: none;
		.mask{
			position: fixed;
			top: 0;
			width: 100%;
			height: 100%;
			z-index: 21;
			background-color: rgba(0, 0, 0, 0.6);
		}
		.layer {
			position: fixed;
			z-index: 22;
			bottom: -70%;
			width: 100%;
			padding: 0;
			height: 70%;
			border-radius: 20upx 20upx 0 0;
			background-color: #fff;
			display: flex;
			flex-wrap: wrap;
			align-content: space-between;
			// 购物车
			.m-shopcar-box {
				width: 100%;
				// padding: 30upx 0;
				.m-header{
					padding: 30upx 30upx;
					display: flex;
					flex-direction: row;
					justify-content: space-between;
					.m-line{
						display: flex;
						color:#333333;
						font-size: 30upx;
						.m-light{
							color:#333333;
							font-size: 22upx;
							padding-left: 10upx;
						}
					}
					.m-clear-car{
						color:#333333;
						font-size:22upx;
					}
				}
				.m-shopcar-item{
					margin-left: 30upx;
					margin-right: 30upx;
					display: flex;
					flex-direction: row;
					justify-content: space-between;
					align-items:center;
					border-top: 1px solid #eee;
					padding: 20upx;
					&:last-of-type{
						border-bottom: 1px solid #eee;
					}
					.m-title{
						color:#4c4c4c;
						font-size: 26upx;
					}
					.m-price{
						color:#ff582b;
						font-size: 26upx;
					}
					.m-controne{
						// flex: 
					}
				}
			}
			.btn {
				width: 100%;
				height: 100upx;
				.button {
					width: 100%;
					height: 80upx;
					border-radius: 40upx;
					color: #fff;
					display: flex;
					align-items: center;
					justify-content: center;
					background-color: #f47952;
					font-size: 28upx;
				}
			}
		}
		
		&.show {
			display: block;
			.mask{
				animation: showPopup 0.2s linear both;
			}
			.layer {
				animation: showLayer 0.2s linear both;
			}
		}
		&.hide {
			display: block;
			.mask{
				animation: hidePopup 0.2s linear both;
			}
			
			.layer {
				animation: hideLayer 0.2s linear both;
			}
		}
		&.none {
			display: none;
		}
		&.service {
			.row {
				margin: 30upx 0;
				.title {
					font-size: 30upx;
					margin: 10upx 0;
				}
				.description {
					font-size: 28upx;
					color: #999;
				}
			}
		}
		&.spec {
			.title {
				font-size: 30upx;
				margin: 30upx 0;
			}
			.sp {
				display: flex;
				view {
					font-size: 28upx;
					padding: 5upx 20upx;
					border-radius: 8upx;
					margin: 0 30upx 20upx 0;
					background-color: #f6f6f6;
					&.on {
						padding: 3upx 18upx;
						border: solid 1upx #f47925;
					}
				}
			}
			.length{
				margin-top: 30upx;
				border-top: solid 1upx #aaa;
				display: flex;
				justify-content: space-between;
				align-items: center;
				padding-top: 20upx;
				.text{
					font-size: 30upx;
				}
				.number{
					display: flex;
					justify-content: center;
					align-items: center;
					.input{
						width: 80upx;
						height: 60upx;
						margin: 0 10upx;
						background-color: #f3f3f3;
						display: flex;
						justify-content: center;
						align-items: center;
						text-align: center;
						input{
							width: 80upx;
							height: 60upx;
							display: flex;
							justify-content: center;
							align-items: center;
							text-align: center;
							font-size: 26upx;
						}
					}
					
					.sub ,.add{
						width: 60upx;
						height: 60upx;
						background-color: #f3f3f3;
						border-radius: 5upx;
						.icon{
							font-size: 30upx;
							width: 60upx;
							height: 60upx;
							display: flex;
							justify-content: center;
							align-items: center;
							
						}
					}
				}
			}
			
		}
	}
	// 商品列表样式
	.category-list{
		width: 100%;
		background-color: #fff;
		display: flex;
		padding-bottom: 99upx;
		
		.left,.right{
			background: #fff;
			position: absolute;
			top: 289upx;
			/*  #ifdef  APP-PLUS  */
			top: calc(100upx + var(--status-bar-height));
			/*  #endif  */
			bottom: 0upx;
		}
		.left{
			width: 24%;
			left: 0upx;
			background-color: #f6f3f3;
			
			.row{
				width: 100%;
				height: 90upx;
				display: flex;
				align-items: center;
				.text{
					width: 100%;
					position: relative;
					font-size: 28upx;
					display: flex;
					justify-content: center;
					color:#999999;
					.block{
						position: absolute;
						width: 0upx;
						left: 0;
					}
				}
				&.on{
					height: 100upx;
					background-color: #fff;
					.text{
						font-size: 30upx;
						// font-weight: 600;
						// color: #2d2d2d;
						.block{
							width: 10upx;
							height: 80%;
							top: 10%;
							// background-color: #f06c7a;
						}
					}
				}
			}
		}
		.right{
		   width: 76%;
			left: 24%;
			.category{
// 				width: 94%;
				padding: 20upx 30upx;
			
				.list{
					margin-top: 40upx;
					width: 100%;
					display: flex;
					flex-wrap: wrap;
					.box{
						width: 100%;
					}
				}
			}
		}
	}
	/*抛物线小球*/
	.good_box{
	  width: 10px;
	  height: 10px;
	  position: fixed;
	  border-radius: 50%;
	  overflow: hidden;
	  left: 50%;
	  top: 50%;
	  z-index: +99;
	  background:#ff582b;
	}
</style>


<template>
	<view class="app-container">
		<view class="top-pic">
			<image style="width: 750rpx; height: 598.798rpx;" src="../../../static/img_top@3x.png" mode="scaleToFill"></image>
		</view>
		
		<view class="button-container">
			<view class="yunshi-and-liucheng">
				<navigator url="../../index/scan/scan">
					<view class="yunshi">
						<image style="width: 300rpx; height: 320rpx;" src="../../../static/img_saoma@3x.png" mode="scaleToFill">
						</image>
						<view class="yunshi-description">
							<text>运势扫码 > </text>
							<view class="yunshi-description-detail">
								<text>点击扫码查看运势</text>
							</view>
						</view>
					</view>
				</navigator>
				<navigator url="../../index/process/process">
					<view class="liucheng">
						<image style="width: 300rpx; height: 320rpx;" src="../../../static/img_liucheng@3x.png" mode="scaleToFill">
						</image>
						<view class="liucheng-description">
							<text>流程演示 > </text>
							<view class="liucheng-description-detail">
								<text>查看占卜演示流程</text>
							</view>
						</view>
					</view>
				</navigator>
				
			</view>
			<view class="advertise">
				<text style="justify-content: center;">新品咖啡上线，九折优惠，进进店品尝！</text>
			</view>
			<view class="news">
				
				<text>news!</text>
			</view>
			<view class="coffee-time">
				<image style="width: 650rpx; height: 172.04rpx;" src="../../../static/img_ad@3x.png" mode="scaleToFill"></image>
			</view>
			<view class="bottom-four-button">
				<view class="bottom-four-single">
					<view>
						<view class="bottom-four-single-detail">
							<image style="width: 80.1rpx; height: 80.1rpx;" src="../../../static/icon_dp@3x.png" mode="scaleToFill">
							</image>
						</view>
						<text>店面介绍</text>
					</view>
					
					
				</view>
				<view class="bottom-four-single">
					<view>
						<view class="bottom-four-single-detail">
							<image style="width: 80.1rpx; height: 80.1rpx;" src="../../../static/icon_pp@3x.png" mode="scaleToFill">
							</image>
						</view>
						<text>品牌介绍</text>
					</view>
				</view>
				<view class="bottom-four-single">
					<view>
						<view class="bottom-four-single-detail">
							<image style="width: 80.1rpx; height: 80.1rpx;" src="../../../static/icon_zm@3x.png 	" mode="scaleToFill">
							</image>
						</view>
						<text>合伙招募</text>
					</view>
				</view>
				<view class="bottom-four-single">
					<view>
						<view class="bottom-four-single-detail">
							<image style="width: 80.1rpx; height: 80.1rpx;" src="../../../static/icon_xx@3x.png" mode="scaleToFill">
							</image>
						</view>
						<text>消息公告</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui'
			}
		},
		methods: {

		}
	}
</script>

<style>
	
	.app-container {
		background-color: #F1F1F0;
	}
	.top-pic {
		background-color: black;
		width: 750rpx;
		height: 598.798rpx;
	}
	.button-container {
		width: 750rpx;
		padding: 50rpx;
		margin-top: -150rpx;
	}
	.yunshi-and-liucheng {
		width: 650rpx;
		height: 300rpx;
		display: flex;
		justify-content: space-between;
	}
	.yunshi {
		width: 300rpx;
		height: 300rpx;
		position: relative;
		/* background: blue; */
		/* background-image: url(../../../static/img_saoma@3x.png); */
	}
	.yunshi-description {
		width: 100%;
		  position:absolute; 
		  z-index:2;
		  left:43.05rpx;
		  top:43.05rpx;
		  font-size: 35rpx;

	}
	.yunshi-description-detail text {
		font-size: 23rpx;
		color: #8E8E8E;
	}
	.liucheng {
		width: 300rpx;
		height: 300rpx;
		position: relative;
		/* background: blue; */
	}
	.liucheng-description {
		width: 100%;
		  position:absolute; 
		  z-index:2;
		  left:43.05rpx;
		  top:43.05rpx;
		  font-size: 35rpx;
	}
	.liucheng-description-detail text {
		font-size: 23rpx;
		color: #8E8E8E;
	}
	.news {
		width: 113rpx;		height: 39.56rpx;		margin-left: 40rpx;		margin-top: -100rpx;		border-top-left-radius: 10rpx;		border-bottom-right-radius: 10rpx;		background-color: #15140F;		text-align:center;		align-items: center;		justify-content: center;		display: flex;		color: #9C6D2E;
	}
	
	.news .text-box {
		margin-bottom: 40rpx;
		padding: 40rpx 0;
		display: flex;
		min-height: 300rpx;
		background-color: #FFFFFF;
		justify-content: center;
		align-items: center;
		text-align: center;
		font-size: 30rpx;
		color: #353535;
		line-height: 1.8;	
	}
	.advertise {
		width: 650rpx;
		height: 84.72rpx;
		margin-top: 50rpx;
		background-color: white;
		border-radius: 20rpx;
		text-align:center;
		justify-content: center;
		display: flex;		align-items: center;
	}
	.coffee-time {
		width: 650rpx;
		height: 172.04rpx;
		margin-top: 110rpx;
		
	}
	.bottom-four-button {
		width: 650rpx; 
		height: 500rpx;
		margin-top: 50rpx;
		display: flex;
		flex-flow:row wrap;
		justify-content: space-between;
	}
	.bottom-four-single {
		width: 305.15rpx;
		height: 202.99rpx;
		background-color: #FFFFFF;
		display: flex;
		border-radius: 30rpx;		justify-content: center;		box-shadow: 1rpx 1rpx 20rpx 20rpx #EBEDF4;
	}
	.bottom-four-single-detail {
		margin-top: 40rpx;
		display: flex;
		justify-content: center;
	}
	
</style>

<template>
	<view v-if="picUrl!== '' " class="app-container">
		<view class="top-pic">
			<image style="width: 750rpx; height: 598.798rpx;" :src="picUrl+'img_top@3x.png'" mode="scaleToFill"></image>
		</view>
		
		<view class="button-container">
			<view class="yunshi-and-liucheng">
				<navigator url="../../index/scan/scan">
					<view class="yunshi">
						<image style="width: 300rpx; height: 320rpx;" :src="picUrl+'img_saoma@3x.png'" mode="scaleToFill">
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
						<image style="width: 300rpx; height: 320rpx;" :src="picUrl+'img_liucheng@3x.png'" mode="scaleToFill">
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
				<image style="width: 650rpx; height: 172.04rpx;" :src="picUrl+'img_ad@3x.png'" mode="scaleToFill"></image>
			</view>
			<view class="bottom-four-button">
				<view class="bottom-four-single" @click="toggle('center')" >
					<view>
						<view class="bottom-four-single-detail">
							<image style="width: 80.1rpx; height: 80.1rpx;" :src="picUrl+'icon_dp@3x.png'" mode="scaleToFill">
							</image>
						</view>
						<text>店面介绍</text>
					</view>
					
					
				</view>
				<view class="bottom-four-single" @click="toggle('center')" >
					<view>
						<view class="bottom-four-single-detail" >
							<image style="width: 80.1rpx; height: 80.1rpx;" :src="picUrl+'icon_pp@3x.png'" mode="scaleToFill">
							</image>
						</view>
						<text>品牌介绍</text>
					</view>
				</view>
				<view class="bottom-four-single" @click="toggle('center')" >
					<view>
						<view class="bottom-four-single-detail">
							<image style="width: 80.1rpx; height: 80.1rpx;" :src="picUrl+'icon_zm@3x.png'" mode="scaleToFill">
							</image>
						</view>
						<text>合伙招募</text>
					</view>
				</view>
				<view class="bottom-four-single" @click="login" >
					<view>
						<view class="bottom-four-single-detail">
							<image style="width: 80.1rpx; height: 80.1rpx;" :src="picUrl+'icon_xx@3x.png'" mode="scaleToFill">
							</image>
						</view>
						<text>消息公告</text>
					</view>
				</view>
			</view>
		</view>
		<!-- 基本示例 -->
		<uni-popup id="popup" ref="popup" :type="popupType" :animation="false" @change="change">
			<view class="popup-content">
				<view class="popup-content-detail">
					<view class="popup-content-pic">
						<image style="width: 326rpx; height: 286rpx;" :src="picUrl+'img_zwnr@3x.png'" mode="scaleToFill" ></image>
					</view>
					<view class="popup-content-text">
						<text>敬请期待</text>
					</view>
					<view class="popup-content-button">
						<view class="popup-content-button-text" @click="closePopup">
							<text>关闭</text>
						</view>
					</view>
				</view>	
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import amap from '@/utils/amap-wx.js';
	import {picUrl as picUrlUtils, apiUrl} from '@/utils/api.js'
	export default {
		data() {
			return {
				href: 'https://uniapp.dcloud.io/component/README?id=uniui',
				popupType: 'center',
				key: '19d2697f69152e1c46d5d5d2c641bc85',
				amapPlugin: null,
				picUrl: '',
				apiUrl: '',
			}
		},
		
		created() {
			
			
		},
		onLoad() {
			// console.log('111')
			// uni.showModal({
			// 	title: '111'
			// })
			this.apiUrl = apiUrl
			this.picUrl = picUrlUtils
			console.log(this.picUrl)
			this.amapPlugin = new amap.AMapWX({
							key: this.key
						});
			console.log('222')
			// uni.showModal({
			// 	title: '222'
			// })
			this.login()
			this.getLocation()
			this.test()
			console.log('333')
		},
		methods: {
			// test
			test() {
				uni.request({
					url: this.apiUrl + 'coffee-xcx/coffee/test/queryPage',
					method: 'POST',
					success: (res) => {
							console.log('res.data')
					        console.log(res.data)
					    }
				})
			},
			// 
			login() {
				// console.log('login')
				// uni.showModal({
				// 	title: 'login'
				// })
				uni.login({
				  provider: 'weixin',
				  success: function (loginRes) {
				 //    console.log(loginRes.authResult);
					// uni.showModal()({
					// 	title: JSON.stringify(loginRes)
					// })
				  },
				  fail: function (loginRes) {
				  	// uni.showTModal()({
				  	// 	title: JSON.stringify(loginRes)
				  	// })
				  }
				});
			},
			// 获取地址
			getLocation() {
				uni.getLocation({
					type: 'wgs84',
					geocode: true,
					success: function (res) {
					    console.log('当前位置的经度：' + res.longitude);
					    console.log('当前位置的纬度：' + res.latitude);
						console.log('accuracy' + res.accuracy)
						console.log('address:')
						
					}
				})
				this.amapPlugin.getRegeo({
									success: (data) => {
										console.log(data)
										console.log(data[0].name)
										console.log(data[0].regeocodeData.formatted_address)
										// this.location = data[0].name;
									},
									fail: err => {
										console.log(err)
									}
								});
			},
			
			/**
			 * 打开基础内容
			 */
			toggle(type) {
				console.log('toggle')
				console.log(this.popupType)
				this.popupType = type
				console.log(this.popupType)
				this.$refs.popup.open()
			},
			/**
			 * popup 状态发生变化触发
			 * @param {Object} e
			 */
			change(e) {
				console.log('popup ' + e.type + ' 状态', e.show)
			},
			// 关闭popup
			closePopup() {
				this.$refs.popup.close()
			}
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
	.popup-content {
		background-color: #fff;
		padding: 15px;
		width: 600rpx;
		height: 666rpx;
		display: flex;
		justify-content: center;
	}
	.popup-content-detail {
		display: flex;
		flex-flow: column;
	}
	.popup-content-pic {
		margin-top: 100rpx;
		/* margin-left: 43.5rpx; */
		/* width: 326rpx;
		height: 286rpx; */
		display: flex;
		justify-content: center;
	}
	.popup-content-text {
		color: #999999;
		font-size: 27rpx;
		margin-top: 65rpx;
		display: flex;
		justify-content: center;
	}
	.popup-content-button {
		margin-top: 45rpx;
		width: 500rpx;
		height: 70rpx;
		background: linear-gradient(to right, #D1A04B , #B28331); 
		border-radius: 35rpx;
		/* position: relative; */
		display: flex;
		align-items: center;
	}
	.popup-content-button-text {
		margin: 0 auto;
		color: #FFFFFF;
		font-size: 29rpx;
	}
</style>

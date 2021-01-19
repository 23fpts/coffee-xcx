<template>
	<view class="app-container">
		<view class="config-item">
			<view class="config-item-pic">
				<image :src="picUrl+'icon_location@3x.png'" style="width: 60rpx; height: 60rpx;" mode="scaleToFill"></image>
			</view>
			<view class="config-item-info">
				<view class="config-item-info-detail">
					<view class="config-item-info-detail-text">
						<text>授权定位</text>
					</view>
					<view class="config-item-info-detail-button">
						<switch @change="GPSSwitchChange" color="#E5AD62" style="transform:scale(0.7)"/>
					</view>
				</view>
			</view>
		</view>
		<view class="config-item">
			<view class="config-item-pic">
				<image :src="picUrl+'icon_img@3x.png'" style="width: 60rpx; height: 60rpx;" mode="scaleToFill"></image>
			</view>
			<view class="config-item-info">
				<view class="config-item-info-detail">
					<view class="config-item-info-detail-text">
						<text>保存相册</text>
					</view>
					<view class="config-item-info-detail-button">
						<switch @change="albumSwitchChange" color="#E5AD62" style="transform:scale(0.7)"/>
					</view>
				</view>
			</view>
		</view>
		<view class="config-item">
			<view class="config-item-pic">
				<image :src="picUrl+'icon_about@3x.png'" style="width: 60rpx; height: 60rpx;" mode="scaleToFill"></image>
			</view>
			<view class="config-item-info">
				<view class="config-item-info-detail">
					<view class="config-item-info-detail-text">
						<text>关于（相关协议）</text>
					</view>
					<view class="config-item-info-detail-button">
						<switch @change="infoSwitchChange" color="#E5AD62" style="transform:scale(0.7)"/>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import {picUrl as picUrlUtils} from '@/utils/api.js'
	export default {
		data() {
			return {
				picUrl: '',
				href: 'https://uniapp.dcloud.io/component/README?id=uniui',
				GPSselected: false,
				albumSelected: false,
				infoSelected: false
			}
		},
		created() {
			this.picUrl = picUrlUtils
		},
		methods: {
			GPSSwitchChange : function (e) {
				this.GPSselected = e.target.value
				
				console.log('switch1 发生 change 事件，携带值为', e.target.value)
			},
			albumSwitchChange: function (e) {
				this.albumSelected = e.target.value
				console.log('switch2 发生 change 事件，携带值为', e.target.value)
			},
			infoSwitchChange: function (e) {
				this.infoSelected = e.target.value
				console.log('switch3 发生 change 事件，携带值为', e.target.value)
			},
	
		}
	}		
</script>

<style>
	.app-container {
		padding: 55rpx;
		padding-top: 0rpx;
		/* background-color: #000000; */
	}
	.config-item {
		/* background-color: #007AFF; */
		width: 640rpx;
		height: 135rpx;
		display: flex;
		justify-content: space-between;
		justify-content: center;
		position: relative;	
		align-items: center;
	}
	.config-item-pic {
		/* background-color: #4CD964; */
		width: 60rpx;
		height: 60rpx;
	}
	.config-item-info {
		/* background-color: #B28331; */
		width: 600rpx;
		height: 135rpx;
		border-bottom: 2rpx solid #CDCDCC;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.config-item-info-detail {
		width: 550rpx;
		height: 60rpx;
		background-color: white;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	.config-item-info-detail-text {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 30rpx;
	}
	.config-item-info-detail-button {
		display: flex;
		justify-content: space-between;
		align-items: center;
		height: 35rpx;
	}
</style>

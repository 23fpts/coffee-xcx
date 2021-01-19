<template>
	<view class="app-container">
		<view class="message-list">
			<view class="message-list-item" v-for="item in list">
				<view class="message-list-item-pic">
					<image :src="item.pic" style="height: 275.51rpx; width: 674rpx;" mode="aspectFill"></image>
				</view>
				<view class="message-list-item-bottom">
					<view class="message-list-item-bottom-text">
						<view class="message-list-item-bottom-title">
							<text>{{item.title}}</text>
						</view>
						<view class="message-list-item-bottom-detail">
							<text>{{item.detail}}</text>
						</view>
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
	            value: 2,
				list: [
					{
						pic: 'https://edu-kex.oss-cn-shanghai.aliyuncs.com/2021/2021011701.jpg',
						title: '意大利脆饼登场，快蘸着咖啡吃',
						detail: '鱼眼咖啡门店，小程序外送+4元即可换购'
					},
					{
						pic: 'https://edu-kex.oss-cn-shanghai.aliyuncs.com/2021/2021011702.jpg',
						title: '咖啡&巧克力礼盒，寒冷冬日用它犒劳自己',
						detail: '鱼眼咖啡天猫旗舰店现已开售'
					},
					{
						pic: 'https://edu-kex.oss-cn-shanghai.aliyuncs.com/2021/2021011703.jpg',
						title: '神仙杯洄游疾患｜10颗空瓶换一颗，长期有效，速来',
						detail: '六号神仙杯冻干即速溶咖啡空瓶，每10颗空瓶即可兑换1颗！'
					},
				]
	        }
	    },
	    methods: {
	        onChange(e) {
	            console.log('rate发生改变:' + JSON.stringify(e))
	        }
	    }
	}
</script>

<style>
	.app-container{
		padding: 39.65rpx;
		background-color: #E7E7E7;
	}
	.message-list {
		background-color: #E7E7E7;
		display: flex;
		flex-flow: column;
	}
	.message-list-item {
		background-color: #FFFFFF;
		margin-bottom: 36.87rpx;
		/* height: 412.596rpx; */
		border-radius: 10rpx;
	}
	.message-list-item-pic {
		/* background-color: red; */
		height: 275.51rpx;
	}
	.message-list-item-bottom {
		/* background-color: green; */
		/* height: 137.059rpx; */
	/* 	display: flex;
		justify-content: center; */
	}
	.message-list-item-bottom-text {
		/* background-color: pink; */
		margin-left: 50rpx;
		/* height: 137.059rpx; */
		display: flex;
		flex-flow: column;
	}
	.message-list-item-bottom-title {
		margin-top: 20rpx;
	}
	.message-list-item-bottom-detail {
		margin-top: 10rpx;
		font-size: 25rpx;
		color: #AEAEAE;
		margin-bottom: 10rpx;
	}
	
</style>

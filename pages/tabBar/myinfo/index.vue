<template>
	<view class="app-container">
		<view class="top-pic">
			<image style="width: 750rpx; height: 439rpx;" :src="picUrl+'img_us_bg@3x.png'" mode="scaleToFill" ></image>
			<view class="Myiu">
				<text>Myiu ></text>
			</view>
			<view class="VIP">普通会员</view>
			<view class="join">加入会员</view>
			<view class="head-pic">
				<image style="height: 74rpx; width: 74rpx;" :src="picUrl+'avatar@3x.png'" mode="scaleToFill"></image>
			</view>
		</view>
		<view class="selected-container">
			<view class="config-item">
				<view class="config-item-pic">
					<image :src="picUrl+'icon_phone@3x.png'" style="width: 60rpx; height: 60rpx;" mode="scaleToFill"></image>
				</view>
				<view class="config-item-info">
					<view class="config-item-info-detail">
						<view class="config-item-info-detail-text">
							<text>手机号</text>
						</view>
						<button class="fast-button" open-type="getPhoneNumber" @getphonenumber="getPhoneNumber">快速绑定</button>
					</view>
				</view>
			</view>
			<view class="config-item">
				<view class="config-item-pic">
					<image :src="picUrl+'icon_shengri@3x.png'" style="width: 60rpx; height: 60rpx;" mode="scaleToFill"></image>
				</view>
				<view class="config-item-info">
					<view class="config-item-info-detail">
						<view class="config-item-info-detail-text">
							<text>生日</text>
						</view>
						<picker mode="date" :value="birthday" @change="bindDateChange">
							<view v-if="!judgeSelected(birthday)" class="info-table-item-detail-bd-unselected">
								<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
							</view>
							<view v-if="judgeSelected(birthday)" class="info-table-item-detail-bd-selected">
								<text>{{birthday}}</text>
								<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
							</view>
						</picker>
					</view>
				</view>
			</view>
			<view class="config-item">
				<view class="config-item-pic">
					<image :src="picUrl+'icon_xingbie@3x.png'" style="width: 60rpx; height: 60rpx;" mode="scaleToFill"></image>
				</view>
				<view class="config-item-info">
					<view class="config-item-info-detail">
						<view class="config-item-info-detail-text">
							<text>性别</text>
						</view>
						<view class="info-table-item-detail-radio">
							<radio-group @change="radioChangeGender">
								<label class="radio"><radio value="1"  color="#B28331"/>男</label>
								<label class="radio"><radio value="2"  color="#B28331"/>女</label>
							</radio-group>
						</view>
					</view>
				</view>
			</view>
			<view class="config-item">
				<view class="config-item-pic">
					<image :src="picUrl+'icon_zhiye@3x.png'" style="width: 60rpx; height: 60rpx;" mode="scaleToFill"></image>
				</view>
				<view class="config-item-info">
					<view class="config-item-info-detail">
						<view class="config-item-info-detail-text">
							<text>职业</text>
						</view>
						<picker @change="bindOccupationChange" :value="occupation" :range="occupationList">
							<view v-if="!judgeSelected(occupation)" class="info-table-item-detail-bd-unselected">
								<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
							</view>
							<view v-if="judgeSelected(occupation)" class="info-table-item-detail-bd-selected">
								<text>{{occupation}}</text>
								<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
							</view>
						</picker>
					</view>
				</view>
			</view>
			<view class="config-item">
				<view class="config-item-pic">
					<image :src="picUrl+'icon_hunyin@3x.png'" style="width: 60rpx; height: 60rpx;" mode="scaleToFill"></image>
				</view>
				<view class="config-item-info">
					<view class="config-item-info-detail">
						<view class="config-item-info-detail-text">
							<text>婚姻状态</text>
						</view>
						<picker @change="bindMarriageChange" :value="marriage" :range="marriageList">
							<view v-if="!judgeSelected(marriage)" class="info-table-item-detail-bd-unselected">
								<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
							</view>
							<view v-if="judgeSelected(marriage)" class="info-table-item-detail-bd-selected">
								<text>{{marriage}}</text>
								<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
							</view>
						</picker>
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
				direction: '',
				direction_selected: 0,
				birthday: '',
				gender: '',
				gender_selected: 0,
				occupation: '',
				occupationList: ['无工作', '找工作', '学生', '老板', '工作中', '退休'],
				marriage: '',
				marriageList: ['单身', '柏拉图式', '复杂的', '恋爱中', '刚分手', '已婚', '离婚']
				
			}
		},
		created() {
			this.picUrl = picUrlUtils
		},
		methods: {
			radioChange(e) {
				// console.log('type:' + e.detail.value)
				this.direction = e.detail.value
				this.direction_selected = e.detail.value+0
			},
			radioChangeGender(e) {
				// console.log('type:' + e.detail.value)
				this.gender = e.detail.value
				this.gender_selected = e.detail.value+0
			},
			getResult() {
				console.log('direction:'+this.direction)
				console.log('birthday:'+this.birthday)
				console.log('gender:'+this.gender)
				console.log('occupation:'+this.occupation)
				console.log('marriage:'+this.marriage)
			},
			judgeSelected(item) {
				if (item === null || item === undefined || item === '') { 
				  // 有值
				  // console.log('false:'+item)
				  return false 
				} else {
					console.log('true:'+item)
				  return true
				}
			},
			// 日期修改
			bindDateChange(e) {
				this.birthday = e.target.value
			},
			// 职业修改
			bindOccupationChange(e) {
				// console.log('value: '+e.target.value)
				// console.log('string: '+this.occupationList[e.target.value])
				this.occupation = this.occupationList[e.target.value]
			},
			bindMarriageChange(e) {
				// console.log('value: '+e.target.value)
				// console.log('string: '+this.occupationList[e.target.value])
				this.marriage = this.marriageList[e.target.value]
			},
			// 手机号
			getPhoneNumber(e) {  
			                console.log(e.detail.errMsg);  
			                console.log(e.detail.iv);  
			                console.log(e.detail.encryptedData);  
			            } 
		}
	}
	

</script>

<style>
	.app-container {
		background-color: white;
	}
	.top-pic {
		background-color: white;
		width: 750rpx;
		height: 439rpx;
	}
	.top-pic {
		background-color: white;
		width: 750rpx;
		height: 439rpx;
	}
	.head-pic {
		width: 74rpx;
		height: 74rpx;
		position: absolute;
		z-index: 2;
		top: 203rpx;
		left: 116rpx;
		
	}
	.Myiu {
		width: 100%;
		position:absolute; 
		z-index:2;
		left:209rpx;
		top:223rpx;
		font-size: 36rpx;
		color: #15140F;
	}
	.VIP {
		width: 100%;
		position:absolute; 
		z-index:2;
		left:284rpx;
		top:298rpx;
		font-size: 46rpx;
		color: #15140F;
	}
	.join {
		width:98rpx;
		height: 29rpx;
		background-color: #413A2D;
		position:absolute; 
		z-index:2;
		left:524rpx;
		top:370rpx;
		font-size: 15.66rpx;
		color:#FFFFFF;
		border-radius: 15rpx;
		align-items: center;
		text-align: center;
		display: flex;
		justify-content: center;
	}
	.selected-container {
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
		height: 30rpx;
	}
	.config-item-info-detail-button {
		height: 35rpx;
	}
	.info-table-item-detail-bd-unselected {
		display: flex;
		justify-content:center;
	}
	
	.info-table-item-detail-bd-selected {
		display: flex;
		justify-content:center;
	}
	.radio radio {
		transform:scale(0.7)
	}
	.fast-button {
		width: 195rpx;
		height: 52rpx;
		background-color: #B39774;
		margin-right: 5rpx;
		margin-top: 25rpx;
		color: white;
		font-size: 24rpx;
		display: flex;
		justify-content: center;
		text-align: center;
		align-items: center;
	}
</style>


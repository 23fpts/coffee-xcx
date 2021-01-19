<template>
	<view class="app-container">
		<view class="top-pic">
			<image :src="picUrl+'img_bg_1@3x.png'" style="width: 750rpx; height: 320rpx;" mode="scaleToFill" ></image>
		</view>
		<view class="top-three-button">
			<view class="top-three-button-single" @click="uploadPicCover">
				<image :src="picUrl+'img_up@3x.png'" style="width: 220rpx; height: 210rpx;" mode="scaleToFill"></image>
				<view class="top-three-button-single-detail">
					<text>上传杯盖照片</text>
				</view>
			</view>
			<view class="top-three-button-single">
				<image :src="picUrl+'img_up_2@3x.png'" style="width: 220rpx; height: 210rpx;" mode="scaleToFill"></image>
				<view class="top-three-button-single-detail">
					<text>上传杯侧照片</text>
				</view>
			</view>
			<view class="top-three-button-single">
				<image :src="picUrl+'img_up_3@3x.png'" style="width: 220rpx; height: 210rpx;" mode="scaleToFill" ></image>
				<view class="top-three-button-single-detail">
					<text>上传杯底照片</text>
				</view>
			</view>
		</view>
		<view class="info-table">
			<view class="info-table-item">
				<view class="info-table-item-detail">
					<text>解析方向</text>
				</view>
				<view class="info-table-item-detail-radio">
					<radio-group @change="radioChange">
						<label class="radio"><radio value="1"  color="#B28331"/>通用</label>
						<label class="radio"><radio value="2"  color="#B28331"/>爱情</label>
						<label class="radio"><radio value="3"  color="#B28331"/>事业</label>
					</radio-group>
				</view>
				
			</view>
			<view class="info-table-item">
				<view class="info-table-item-detail">
					<text>出生日期</text>
					
				</view>
				<view class="info-table-item-detail-bd">
					<picker mode="date" :value="birthday" @change="bindDateChange">
						<view v-if="!judgeSelected(birthday)" class="info-table-item-detail-bd-unselected">
							<text>选择出生日期</text>
							<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
						</view>
						<view v-if="judgeSelected(birthday)" class="info-table-item-detail-bd-selected">
							<text>{{birthday}}</text>
							<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
						</view>
					</picker>
					
					
				</view>
			</view>
			<view class="info-table-item">
				<view class="info-table-item-detail">
					<text>性别</text>
				</view>
				<view class="info-table-item-detail-radio">
					<radio-group @change="radioChangeGender">
						<label class="radio"><radio value="1"  color="#B28331"/>男</label>
						<label class="radio"><radio value="2"  color="#B28331"/>女</label>
					</radio-group>
				</view>
			</view>
			<view class="info-table-item">
				<view class="info-table-item-detail">
					<text>职业</text>
				</view>
				<view class="info-table-item-detail-bd">
					<picker @change="bindOccupationChange" :value="occupation" :range="occupationList">
						<view v-if="!judgeSelected(occupation)" class="info-table-item-detail-bd-unselected">
							<text>选择职业</text>
							<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
						</view>
						<view v-if="judgeSelected(occupation)" class="info-table-item-detail-bd-selected">
							<text>{{occupation}}</text>
							<image :src="picUrl+'icon_left@3x.png'" style="width: 40rpx; height: 40rpx;" mode="scaleToFill"></image>
						</view>
					</picker>
				</view>
			</view>
			<view class="info-table-item">
				<view class="info-table-item-detail">
					<text>婚姻状态</text>
					
				</view>
				<view class="info-table-item-detail-bd">
					<picker @change="bindMarriageChange" :value="marriage" :range="marriageList">
						<view v-if="!judgeSelected(marriage)" class="info-table-item-detail-bd-unselected">
							<text>选择婚姻状态</text>
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
		<view class="result-button">
			<view class="result-button-text" @click="getResult">
				<text>运势解析</text>
			</view>
		</view>
		
	</view>
</template>

<script>
	import {picUrl as picUrlUtils, apiUrl as apiUrlUtils} from '@/utils/api.js'
	export default {
		data() {
			return {
				picUrl: '',
				apiUrl: '',
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
			this.apiUrl = apiUrlUtils
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
				uni.navigateTo({
				            // url: 'test?id=1&name=uniapp'  c传递参数
				
				            url:"/pages/index/result/result"
				
				        })
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
			// 上传
			uploadPic() {
				uni.chooseImage({
				    success: (chooseImageRes) => {
				        const tempFilePaths = chooseImageRes.tempFilePaths;
				        const uploadTask = uni.uploadFile({
				            url: this.apiUrl +'coffee-xcx/files', //仅为示例，非真实的接口地址
				            filePath: tempFilePaths[0],
				            name: 'file',
				            success: (uploadFileRes) => {
				                console.log(uploadFileRes.data);
				            }
				        });
				
				        uploadTask.onProgressUpdate((res) => {
				            console.log('上传进度' + res.progress);
				            console.log('已经上传的数据长度' + res.totalBytesSent);
				            console.log('预期需要上传的数据总长度' + res.totalBytesExpectedToSend);
				
				            // 测试条件，取消上传任务。
				            // if (res.progress > 50) {
				            //     uploadTask.abort();
				            // }
				        });
				    }
				});
			},
			uploadPicCover () {
				this.uploadPic()
			}
		}
	}
</script>

<style>
	.app-container {
		background-color: #F8F8F8;
	}

	.top-pic {
		width: 750rpx;
		height: 320rpx;
	}
	.top-three-button {
		width: 710rpx;
		height: 250rpx;
		margin-left: 20rpx;
		margin-top: -123rpx;
		display: flex;
		justify-content: space-between;
	}
	.top-three-button-single {
		width: 220rpx;
		height: 210rpx;
		position: relative;
		/* box-shadow: 0rpx 0rpx 20rpx 0rpx #A8A8A6; */
	}
	.top-three-button-single-detail {
		width: 100%;
		  position:absolute; 
		  z-index:2;
		  left:40rpx;
		  top:148rpx;
		  font-size: 23rpx;
	}
	.info-table {
		width: 750rpx;
		height: 533rpx;
		background-color: white;
	}
	.info-table-item {
		width: 650rpx;
		height: 66.6rpx;
		background-color: white;
		padding-top: 20rpx;
		padding-left: 50rpx;
		padding-bottom: 20rpx;
		padding-right: 50rpx;
		display: flex;
		flex-flow: row nowrap;
		justify-content: space-between;
		position: relative;
		align-items: center;
		border: 0.5rpx #EDEDED solid;
	}
	.info-table-item-detail {
		background-color: white;
		font-size: 29rpx;
		color: #15140F;
	}
	.info-table-item-detail-radio {
		background-color: white;
		font-size: 29rpx;
		margin-left: 66rpx;
		color: #15140F;
	}
	
	.info-table-item-detail-bd {
		background-color: white;
		font-size: 29rpx;
		/* margin-left: 66rpx; */
		color: #929292;
		display: flex;
		justify-content:center;
	}
	
	.info-table-item-detail-bd-unselected {
		display: flex;
		justify-content:center;
	}
	
	.info-table-item-detail-bd-selected {
		display: flex;
		justify-content:center;
	}
	.result-button {
		margin-top: 45rpx;
		width: 690rpx;
		height: 80rpx;
		margin-left: 30rpx;
		background: linear-gradient(to right, #D1A04B , #B28331); 
		border-radius: 10rpx;
		position: relative;
		display: flex;
		align-items: center;
	}
	.result-button-text {
		margin: 0 auto;
		color: #FFFFFF;
		font-size: 32rpx;
	}
	
	.radio radio {
		transform:scale(0.7)
	}
	
</style>

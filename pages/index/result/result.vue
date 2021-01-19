<template>
	
	<view style="background-color: #15140F;">
		<view style="width: 750rpx; height: 320rpx;">
			<image style="width: 750rpx; height: 320rp;" :src="picUrl+'img_bg_1@3x.png'" mode="scaleToFill"></image>
		</view>
		<view class="sentence">
			<image style="width: 750rpx; height: 751rpx;" :src="picUrl+'img_yunshi_bg@3x.png'" mode="scaleToFill"></image>
			<view class="transformation">
				<text :decode="true" style="color:#9C6D2E;font-weight:bold;" space="nbsp">{{title}}</text>
			</view>
			<view class="yunshi">
				<text style="font-weight: bold;color:#9C6D2E">运势解析</text>
			</view>
			<view class="yunshi2">
				<text :decode="true" style="color:#9C6D2E;" space="nbsp">{{littleTitle}}</text>
			</view>
		</view>
		<view class="evaluate">
			<image style="width: 649.1rpx; height: 537.2rpx;" :src="picUrl+'icon_pingjia_bg@3x.png'" mode="scaleToFill"></image>
			<view class="pingjia">
				<text>评价</text>
			</view>
			<view class="stars">
				<uni-rate v-model="value" @change="onChange"/>
			</view>
			<view class="pingjia3">
				<input class="inputText" auto-focus="true" placeholder="请您点评一下~"  />
			</view>
			
            <checkbox-group class="guaci">
                <label>
                    <checkbox value="save" style="font-size: 30rpx;"/>保存卦辞</checkbox>
                </label>
            </checkbox-group>
			
			<button class="commit-button">提交评价</button>
			
		</view>
	</view>
</template>

<script>
	
	import {picUrl as picUrlUtils} from '@/utils/api.js'
	Page({
	  data: {
	    focus: false,
	    inputValue: ''
	  },
	  bindKeyInput: function (e) {
	    this.setData({
	      inputValue: e.detail.value
	    })
	  },
	  bindReplaceInput: function (e) {
	    var value = e.detail.value
	    var pos = e.detail.cursor
	    var left
	    if (pos !== -1) {
	      // 光标在中间
	      left = e.detail.value.slice(0, pos)
	      // 计算光标的位置
	      pos = left.replace(/11/g, '2').length
	    }
	
	    // 直接返回对象，可以对输入进行过滤处理，同时可以控制光标的位置
	    return {
	      value: value.replace(/11/g, '2'),
	      cursor: pos
	    }
	
	    // 或者直接返回字符串,光标在最后边
	    // return value.replace(/11/g,'2'),
	  },
	  bindHideKeyboard: function (e) {
	    if (e.detail.value === '123') {
	      // 收起键盘
	      wx.hideKeyboard()
	    }
	  }
	})
	
	export default {
		    
		    data() {
		        return {
					picUrl: '',
		            value: 2,
					gender: '',
					gender_selected: 0,	
					save:'',
					title: '\t &nbsp;&nbsp;&nbsp; 你心中的那个人，真的适合你吗？你们能够一起携手到老吗？关于你们能否走到最后，其实你心理有了答案！',
					littleTitle:' \t &nbsp;&nbsp;&nbsp; jessica，您好！你心中的那个人，真的适合你吗？你们能够一起携手到老吗？关于你们能否走到最后，其实你心理有了答案！',
					rank:2,
					review:''
					
		        }
		    },
			created() {
				this.picUrl = picUrlUtils
				console.log('123123')
				console.log(this.title)
			},
		    methods: {
		        onChange(e) {
		            console.log('rate发生改变:' + JSON.stringify(e))
		        }
		    }
		}
</script>
<style>
	.sentence {
		width: 750rpx;
		height: 751rpx;
		margin-top:-160rpx;
		position: relative;

	}
	.transformation {
		width: 490rpx;
		height: 187rpx;
		font-size: 35rpx;
		position: absolute;
		/* text-align: center; */
/* 		display: flex; */
		/* align-items: center; */
/* 		justify-content: center; */
		text-overflow:ellipsis;
		word-wrap:break-word;
		left:124rpx;
		top:118rpx;
		text-align: justify;
		text-justify:inter-ideograph;
		text-align-last:left;
	}
	.evaluate {
		width: 649.1rpx;
		height: 537.2rpx;
		margin-top: 19rpx;
		margin-left: 52rpx;
	}
	.yunshi {
		width: 124rpx;
		height: 30rpx;
		position: absolute;
		font-size: 30rpx;
		top: 473rpx;
		left: 115rpx;
	}
	.yunshi2 {
		
		width: 510rpx;
		height: 108rpx;
		font-size: 24rpx;
		position: absolute;
		/* text-align: center; */
/* 		display: flex; */
		/* align-items: center; */
/* 		justify-content: center; */
		text-overflow:ellipsis;
		word-wrap:break-word;
		left:114rpx;
		top:533rpx;
		text-align: justify;
		text-justify:inter-ideograph;
		text-align-last:left;
	}
	.pingjia {
		width: 73rpx;
		height: 29rpx;
		font-size: 30rpx;
		color: #9C6D2E ;
		position: absolute;
		top: 946rpx;
		left: 96rpx;
		font-weight: bold;
		text-align: center;
		position: absolute;
	}
	.commit-button {
		width: 538rpx;
		height: 80rpx;
		
		left: 111rpx;
		top: 1300rpx;
		color: white;
		font-size: 30rpx;
		color: white;
		display: flex;
		justify-content: center;
		text-align: center;
		align-items: center;
		position: absolute;
		border-radius: 35rpx;
		background: linear-gradient(to right, #D1A04B , #B28331); 
	}
	.inputText {
		font-size: 30rpx;
		width: 580rpx;
		height: 60rpx;
		font-family:'微软雅黑';
		text-overflow:ellipsis;
		word-wrap:break-word;
		background: #F8F8F8;
		position: absolute;
		color: #9C6D2E;
	}
	.pingjia3 {
		width: 580rpx;
		height: 189.5rpx;
		top: 1030rpx;
		left: 87rpx;
		background-color: #F8F8F8;
/* 		display: flex;
		justify-content: center; */
		position: absolute;
/* 		text-align: center;
		align-items: center; */


	}
	
	.evaluate {
		color:#9C6D2E;
		font-family:'微软雅黑';
		font-size: 24rpx;

	}
	.stars {
		width: 301rpx;
		height: 58rpx;
		position: absolute;
		top: 946rpx;
		left: 208rpx;
	}
	.radio radio {
		transform:scale(0.7)
	}
	.guaci {
		width: 200rpx;
		height: 28rpx;
		left: 100rpx;
		top: 1220rpx;
		position: absolute;
		
	}

</style>
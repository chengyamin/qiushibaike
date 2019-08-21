<template>
	<view class="papar-left-popup-mask" v-show="show" @tap="hidepopup">
		<view class="papar-left-popup" v-show="show">
			<view class="u-f-ac" hover-class="papar-left-popup-h" @tap="addfriend">
				<view class="icon iconfont icon-sousuo"></view>
				加好友
			</view>
			<view class="u-f-ac" hover-class="papar-left-popup-h" @tap="clear">
				<view class="icon iconfont icon-qingchu"></view>
				清除缓存
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			show:Boolean
		},
		methods:{
			addfriend(){
				this.$emit('addfriend')
			},
			hidepopup(){
				this.$emit('hide')
			},
			clear(){
				this.$emit('clear')
			}
		}
	}
</script>

<style scoped>
	.papar-left-popup-mask{
		position:fixed;
		top:0;
		bottom:0;
		left:0;
		right:0;
		z-index:1999;
	}
	.papar-left-popup{
		position:fixed;
		right:0;
		top:10upx;
		background:#FFFFFF;
		z-index:2000;
		width:55%;
		box-shadow: 1upx 1upx 20upx 2upx #CCCCCC;
	}
	.papar-left-popup>view{
		padding:20upx;
		font-size:35upx;
	}
	.papar-left-popup>view>view{
		margin-right:10upx;
		font-weight: bold;
	}
	.papar-left-popup-h{
		background: #EEEEEE;
	}
</style>

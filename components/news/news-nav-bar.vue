<template>
	<uni-nav-bar :fixed="true" :statusBar="true" @click-right="openAdd">
		<!-- 左边 -->
		<block slot="left">
			<view class="nav-left">
				<view class="icon iconfont icon-qiandao"></view>
			</view>
		</block>
		<!-- 中间 -->
		<view class="nav-tab-bar u-f-ajc">
			<block v-for="(tab,index) in tabBars" :key="tab.id">
				<view class="u-f-ajc" :class="{'active':tabIndex==index}" @tap="changeTab(index)">
					{{tab.name}}
					<view class="nav-tab-bar-line" v-if="tabIndex==index"></view>
				</view>
			</block>
		</view>
		<!-- 右边 -->
		<block slot="right u-f-ajc">
			<view class="nav-right">
				<view class="icon iconfont icon-bianji1"></view>
			</view>
		</block>
	</uni-nav-bar>
</template>

<script>
	import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue';
	export default {
		components:{
			uniNavBar
		},
		props:{
			tabBars:Array,
			tabIndex:Number
		},
		data(){
			return{
				
			}
		},
		methods:{
			changeTab(index){
				this.$emit('change-tab',index)
			},
			//打开发布页
			openAdd(){
				uni.navigateTo({
					url: '../add-input/add-input',
				});
			}
		}
	}
</script>

<style scoped>
	.nav-left>view,.nav-right>view{
		font-size: 40upx;
	}
	.nav-left>view{
		color:#FF9619;
	}
	.nav-right>view{
		color:#000000;
	}
	.nav-left{
		margin-left:16upx;
	}
	.nav-right{
		width:100%;
	}
	.nav-tab-bar{
		width:100%;
		margin-left: -20upx;
		position:relative;
	}
	.nav-tab-bar>view{
		font-size:30upx;
		padding:0 15upx;
		font-weight: bold;
		color:#969696;
		margin-top:10upx;
	}
	.active{
		color:#333333!important;
	}
	.nav-tab-bar-line{
		border-bottom:5upx solid #FEDE33;
		border-top:5upx solid #FEDE33; 
		width:70upx;
		border-radius: 20upx;
		position: absolute;
		bottom:0upx;
	}
	
</style>

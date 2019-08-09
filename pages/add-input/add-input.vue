<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="back"  @click-left="back" @click-right="submit">
			<view class="u-f-ajc" @tap="changelook">
				{{yinsi}}
				<view clas="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		<!-- 多行输入框 -->
		<view class="uni-textarea">
			<textarea v-model="text" placeholder="说一句话吧~"/>
		</view>
		<!-- 上传多图 -->
		<upload-images @upload="upload"></upload-images>
		<!-- 弹出公告 -->
		<view class="custom-pop" v-if="showCusPop">
			<!-- <view class="tankuang">
				<view class="u-f-ajc">
					<image src="../../static/addinput.png"></image>
				</view>
				<view>1.涉及黄色，政治，广告及骚扰信息</view>
				<view>2.涉及黄色，政治，广告及骚扰信息</view>
				<view>3.涉及黄色，政治，广告及骚扰信息</view>
				<view>一经核实将被封禁，情节严重者永久封禁</view>
				<button type="default" @click="handleCusClick">朕知道了</button>
			</view> -->
		</view>
	</view>
</template>

<script>
	import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue';
	import uploadImages from '../../components/common/upload-images.vue';
	import uniPopup from '../../components/uni-popup/uni-popup.vue';
	
	let changelook=['所有人可见', '仅自己可见'];
	export default {
		components:{
			uniNavBar,
			uploadImages,
			uniPopup
		},
		data() {
			return {
				isget:false,
				yinsi:"所有人可见",
				text:'',
				imglist:[],
				showCusPop: true,
			}
		},
		onBackPress() {
			//如果有评论
			if(!this.text && this.imglist.length<1){return;}
			if(!this.isget){
				this.baocun(); 
				return true;
			}
		},
		methods: {
			
			//保存为草稿
			baocun(){
				uni.showModal({
					content: '是否要存为草稿？',
					cancelText: '不保存',
					confirmText: '保存',
					success: res => {
						if(res.confirm){
							console.log('保存')
						}else{
							console.log('不保存')
						}
						this.isget=true;
						uni.navigateBack({
							delta: 1
						})
					},  
				})
			},
			//返回
			back(){
				uni.navigateBack({
					delta: 1
				});
			},
			//发布
			submit(){
				console.log("发布")
			},
			//隐私
			changelook(){
				console.log("隐私")
				uni.showActionSheet({
					itemList:changelook,
					success: (res)=> {
						// console.log('选中了第' + (res.tapIndex + 1) + '个按钮');
						this.yinsi=changelook[res.tapIndex];
					}
				});
			},
			upload(arr){
				this.imglist=arr;
				console.log(this.imglist);
			},
			handleCusClick(){
				this.showCusPop = false;
			}
		}
	}
</script>

<style>
	.uni-textarea{
		border:1upx solid #EEEEEE;
	}
	.custom-pop {
		width: 100%;
		height: 100%;
		background: #808080;
		position: relative;
		top:0;
		left:0;
	}
	.custom-pop tankuang{
		width:50%;
		height: 50%;
		position: fixed;
		top:50%;
		left:50%;
	}
	.custom-pop button{
		background:#FFE934 ;
	}
</style>

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
			<textarea placeholder="说一句话吧~"/>
		</view>
		<!-- 上传多图 -->
		<upload-images @upload="upload"></upload-images>
	</view>
</template>

<script>
	import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue';
	import uploadImages from '../../components/common/upload-images.vue';
	
	let changelook=['所有人可见', '仅自己可见'];
	export default {
		components:{
			uniNavBar,
			uploadImages
		},
		data() {
			return {
				yinsi:"所有人可见",
				imglist:[]
			}
		},
		methods: {
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
			}
		}
	}
</script>

<style>
	.uni-textarea{
		border:1upx solid #EEEEEE;
	}
	
</style>

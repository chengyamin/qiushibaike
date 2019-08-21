<template>
	<view :border="false" class="common-list u-f animated rotateIn">
		<view class="comoon-list-l">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
		<view class="comoon-list-r">
			<view class="u-f-ac u-f-jsb">
				<view class="u-f-ac">
					{{item.username}}
					<!-- 年龄性别组件 -->
					<tag-sex-age :sex="item.sex" :age="item.age"></tag-sex-age>
				</view>
				<view v-show="!isguanzhu" class="icon iconfont icon-zengjia" @tap="guanzhu">
					关注
				</view>
			</view>
			<view>{{item.title}}</view>
			<view class="u-f-ajc">
				<!-- 图片 -->
				<image v-if="item.titlepic" :src="item.titlepic" mode="widthFix" lazy-load></image>
				<!-- 视频 -->
				<template v-if="item.video">
					<view class="common-list-play icon iconfont icon-bofang"></view>
					<view class="common-list-playinfo">
						{{item.video.looKnum}} 次播放 {{item.video.long}}
					</view>
				</template>
				
				<!-- 分享 -->
				<view v-if="item.share" class="common-list-share u-f-ac">
					<image :src="item.share.titlepic" mode="widthFix" lazy-load></image>
					<view>{{item.share.title}}</view>
				</view>
			</view>
			<view class="u-f-ac u-f-jsb">
				<view>{{item.share.path}}</view>
				<view class="u-f-ac">
					<view class="icon iconfont icon-zhuanfa">{{item.sharenum}}</view>
					<view class="icon iconfont icon-pinglun1">{{item.commentnum}}</view>
					<view class="icon iconfont icon-dianzan1">{{item.goodnum}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import tagSexAge from './tag-sex-age.vue';
	export default {
		props:{
			item:Object,
			index:Number,
			tagSexAge
		},
		data(){
			return{
				isguanzhu:this.item.isguanzhu,
				
			}
		},
		methods:{
			guanzhu(){
				this.isguanzhu=true;
				uni.showToast({
					title: '关注成功'
				});
			}
		}
	}
</script>

<style scoped>
	/* 动态列表 */
	.comoon-list-l image{
		width:90upx;
		height: 90upx;
		border-radius: 100%;
	}
	.comoon-list-l{
		 flex-shrink: 0;/*防止标题被压缩 */
	}
	.common-list{
		padding:20upx;
	}
	.comoon-list-r>view:nth-child(3)>image{
		width:100%;
		border-radius: 10upx;
	}
	.comoon-list-r{
		flex:1;/* 填满剩余空间 */
		margin-left:15upx;
		border-bottom: 1upx solid #EEEEEE;
		padding-bottom:10upx;
	}
	.comoon-list-r>view:nth-child(1)>view:first-child{
		color:#999999;
		font-size: 28upx;
	}
	
	.comoon-list-r>view:nth-child(1)>view:last-child{
		background: #EEEEEE;
		font-size: 26upx;
		padding:0 10upx;
	}
	.comoon-list-r>view:nth-child(2){
		font-size: 32upx;
		padding:12upx 0;
	}
	.comoon-list-r>view:nth-child(3){
		position: relative;
		margin-bottom: 10upx;
	}
	.common-list-play,.common-list-playinfo{
		position: absolute;
		color:#FFFFFF;
	}
	.common-list-play{
		font-size: 100upx;
	}
	.common-list-playinfo{
		right:10upx;
		bottom:10upx;
		background: rgba(51,51,51,0.73);
		border-radius: 20upx;
		padding:0 20upx;
		font-size: 26upx;
	}
	.comoon-list-r>view:nth-child(4)>view{
		color:#AAAAAA;
	}
	.comoon-list-r>view:nth-child(4)>view:nth-child(2)>view:nth-child(2){
		margin:0 15upx;
		font-size:28upx;
	}
	/* 分享 */
	.common-list-share{
		background:#EEEEEE;
		border:1upx solid #EEEEEE;
		width:100%;
		pading:10upx;
		border-radius: 10upx;
	}
	.common-list-share>image{
		width:200upx;
		height:150upx;
		margin-right: 10upx;
	}
</style>

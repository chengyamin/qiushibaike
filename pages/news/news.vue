<template>
	<view>
		<!-- 自定义导航栏 -->
		<news-nav-bar :tabBars="tabBars" :tabIndex="tabIndex" @change-tab="changeTab"></news-nav-bar>
		<!-- 动态列表 -->
		
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight+'px'}" :current="tabIndex" @change="tabChange">
				<!-- 关注 -->
				<swiper-item>
					<scroll-view scroll-y class="list" @scrolltolower="loadmore()">
						<block v-for="(item,index) in guanzhu.list" :key="index">
							<common-list :item="item" :index="index"></common-list>
						</block>
						<!-- 上拉加载 -->
						<load-more :loadtext="guanzhu.loadtext"></load-more>
					</scroll-view>
				</swiper-item>
				<!-- 话题 -->
				<swiper-item>
					<scroll-view scroll-y class="list">
						<!-- 搜索框 -->
						<view class="search-input">
							<input class="uni-input" placeholder-class="icon iconfont icon-sousuo topic-search" placeholder="搜索内容"/>
						</view>
						<!-- 轮播图 -->
						<swiper class="topic-swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
							<block v-for="(item,index) in topic.swiper" :key="index">
								<swiper-item>
									<image :src="item.src" mode="widthFix" lazy-load></image>
								</swiper-item>
							</block>
						</swiper>
						<!-- 热门分类 -->
						<topic-nav :nav="topic.nav"></topic-nav>
						<!-- 最近更新 -->
						<view class="topic-new">
							<view>最近更新</view>
								<block v-for="(item,index) in topic.list" :key="index">
									<topic-list :item="item" :index="index"></topic-list>
								</block>
								
							
						</view>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	
	import commonList from '../../components/common/common-list.vue';
	import newsNavBar from '../../components/news/news-nav-bar.vue';
	import loadMore from '../../components/common/load-more.vue';
	import topicNav from '../../components/news/topic-nav.vue';
	import topicList from '../../components/news/topic-list.vue';
	
	export default {
		components:{
			commonList,
			newsNavBar,
			loadMore,
			topicNav,
			topicList
		},
		data() {
			return {
				swiperHeight:500,
				tabIndex:0,
				tabBars:[
					{name:"关注",id:"guanzhu"},
					{name:"话题",id:"topic"}
				],
				guanzhu:{
					loadtext:"上拉加载更多",
					list:[
						//文字
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"哈哈哈",
							sex:0,//0男1女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"",
							video:false,
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						},
						//图文
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"哈哈哈",
							sex:0,//0男1女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"../../static/demo/datapic/13.jpg",
							video:false,
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						},
						//视频
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"哈哈哈",
							sex:0,//0男1女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"../../static/demo/datapic/13.jpg",
							video:{
								looKnum:"20w",
								long:"2:47"
							},
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						},
						//分享
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"哈哈哈",
							sex:0,//0男1女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"",
							video:false,
							share:{
								title:"我是分享的标题",
								titlepic:"../../static/demo/datapic/14.jpg"
							},
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						}
					]
				},
				topic:{
					swiper:[
						{src:"../../static/demo/banner2.jpg"},
						{src:"../../static/demo/banner2.jpg"},
						{src:"../../static/demo/banner2.jpg"}
					],
					nav:[
						{name:"最新"},
						{name:"游戏"},
						{name:"打卡"},
						{name:"情感"},
						{name:"故事"},
						{name:"喜爱"}
					],
					list:[
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						},
						{
							titlepic:"../../static/demo/topicpic/13.jpeg",
							title:"话题名称",
							desc:"话题描述",
							totalnum:50,
							todaynum:10
						}
					]
				}
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success:(res)=>{
					// console.log(res.windowHeight);
					let height=res.windowHeight-uni.upx2px(100);
					console.log(height);
					this.swiperHeight=height;
				}
			});
		},
		methods: {
			//点击切换
			changeTab(index){
				this.tabIndex=index;
			},
			tabChange(e){
				//滑动事件
				console.log(JSON.stringify(e.detail));
				this.tabIndex=e.detail.current;
			},
			//上拉加载
			loadmore(){
				if(this.guanzhu.loadtext!="上拉加载更多"){
						return;
					}
					//修改状态
					this.guanzhu.loadtext="加载中...";
					//获取数据
					setTimeout(()=>{
						//获取完成
						let obj={
							userpic:"../../static/demo/userpic/12.jpg",
							username:"哈哈哈",
							sex:0,//0男1女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"",
							video:false,
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						};
						this.guanzhu.list.push(obj);
						this.guanzhu.loadtext="上拉加载更多";
					},1000)
					// this.guanzhu.loadtext="没有更多数据了";
				},			
		}
	}
</script>

<style>
.search-input{
	padding:20upx;
}
.search-input>input{
	background: #F4F4F4;
	border-radius: 10upx;
}
.topic-search{
	display: flex;
	justify-content: center;
	font-size:27upx;
}
/* 轮播图 */
.topic-swiper{
	padding:0 20upx 20upx 20upx;
}
.topic-swiper image{
	width:100%;
	border-radius: 10upx;
}
/*  */

</style>

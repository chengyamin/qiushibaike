<template> 
	<view>
		
		
		<!-- 顶部选项卡 -->
		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swiper-tab-head>
		<!--  -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height:swiperHeight+'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items,index) in newslist" :key="index">
					<scroll-view scroll-y class="list" @scrolltolower="loadmore(index)">
						<template v-if="items.list.length>0">
							<!-- 话题列表 -->
							<view class="topic-view">
								<block v-for="(item,index1) in items.list" :key="index1">
									<topic-list :item="item" :index="index1"></topic-list>
								</block> 
							</view>
							<!-- 上拉加载更多 -->
							<load-more :loadtext="items.loadtext"></load-more>
						</template>
						<template v-else>
							<!-- 无内容列表 -->
							<no-thing></no-thing>
						</template>
						
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		
		
	</view>
</template>

<script>
	import swiperTabHead from "../../components/index/swiper-tab-head.vue"
	import loadMore from '../../components/common/load-more.vue';
	import noThing from '../../components/common/no-thing.vue';
	import topicList from '../../components/news/topic-list.vue';
	
	export default {
		components:{
			swiperTabHead,
			loadMore,
			noThing,
			topicList
		},
		data() {
			return {
				swiperHeight:500,
				tabIndex:0,
				tabBars:[
					{
						name:"关注",id:"guanzhu"
					},
					{
						name:"推荐",id:"tuijian"
					},
					{
						name:"体育",id:"tiyu"
					},
					{
						name:"热点",id:"redian"
					},
					{
						name:"财经",id:"caijing"
					},
					{
						name:"娱乐",id:"yule"
					}
				],
				newslist:[
					{
						loadtext:"上拉加载更多",
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
							},{
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
					},
					{
						loadtext:"上拉加载更多",
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
							}
						]
					},
					{
						loadtext:"上拉加载更多",
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
							}
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[]
					},
					{
						loadtext:"上拉加载更多",
						list:[]
					},
					{
						loadtext:"上拉加载更多",
						list:[]
					}
				],
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
		//监听搜素框点击事件
		// onNavigationBarSearchInputClicked() {
		// 	console.log(123);
		// 	uni.navigateTo({
		// 		url: '../search/search',
		// 	});
		// },
		//监听原生标题导航按钮点击事件
		// onNavigationBarButtonTap(e){
		// 	console.log(JSON.stringify(e));
		// 	uni.navigateTo({
		// 		url: '../add-input/add-input',
		// 	});
		// },
		methods: {
			//上拉加载
			loadmore(index){
				if(this.newslist[index].loadtext!="上拉加载更多"){
					return;
				}
				//修改状态
				this.newslist[index].loadtext="加载中...";
				//获取数据
				setTimeout(()=>{
					//获取完成
					let obj={
						titlepic:"../../static/demo/topicpic/13.jpeg",
						title:"话题名称",
						desc:"话题描述",
						totalnum:50,
						todaynum:10
					};
					this.newslist[index].list.push(obj);
					this.newslist[index].loadtext="上拉加载更多";
				},1000)
				// this.newslist[index].loadtext="没有更多数据了";
			},
			tabtap(index){
				//tabbar点击事件
				console.log(index);
				this.tabIndex=index;
			},
			tabChange(e){
				//滑动事件
				console.log(JSON.stringify(e.detail));
				this.tabIndex=e.detail.current;
			}
		}
	}
</script>

<style>
	.topic-view{
		padding:0 20upx;
	}
	
</style>

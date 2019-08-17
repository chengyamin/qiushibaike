<template>
	<view>
		<!-- 话题介绍 -->
		<topic-info :item="topicInfo"></topic-info>
		<!-- tabbar切换 -->
		<swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap" scrollStyle="border-bottom:0;" scrollItemStyle="width:50%;"></swiper-tab-head>
		<!-- 列表 -->
		<view class="topic-detail-list">
			<block v-for="(item,index) in tablist" :key="index">
				<template v-if="tabIndex==index">
					<!-- 列表 -->
					<block v-for="(list,listindex) in item.list" :key="listindex">
						<common-list :item="list" :index="listindex"></common-list>
					</block>
					<!-- 上拉加载 -->
					<load-more :loadtext="item.loadtext"></load-more>
				</template>
			</block>
		</view>
		<index-list ></index-list>
	</view>
</template>

<script>
	import topicInfo from '../../components/topic/topic-info.vue';
	import swiperTabHead from "../../components/index/swiper-tab-head.vue";
	import commonList from '../../components/common/common-list.vue';
	import loadMore from '../../components/common/load-more.vue';
	
	export default {
		components:{
			topicInfo,
			swiperTabHead,
			commonList,
			loadMore
		},
		data() {
			return {
				topicInfo:{
					titlepic:"../../static/demo/topicpic/13.jpeg",
					title:"忆往事，敬余生",
					totalnum:1000,
					todaynum:1000,
					desc:"我是描述"
				},
				tabIndex:0,
				tabBars:[
					{
						name:"默认",id:"moren"
					},
					{
						name:"最新",id:"zuixin"
					}
				],
				tablist:[
					{
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
							}
						]
					},
					{
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
							}
						]
					}
				]
			}
		},
		//上拉触底事件
		onReachBottom(){
			//上拉加载更多
			this.loadmore();
		},
		//监听下拉刷新
		onPullDownRefresh(){
			//下拉刷新
			this.getdata();
		},
		methods: {
			tabtap(index){
				//tabbar点击事件
				console.log(index);
				this.tabIndex=index;
			},
			//上拉加载逻辑
			loadmore(){
				if(this.tablist[this.tabIndex].loadtext!="上拉加载更多"){
					return;
				}
				//修改状态
				this.tablist[this.tabIndex].loadtext="加载中...";
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
					this.tablist[this.tabIndex].list.push(obj);
					this.tablist[this.tabIndex].loadtext="上拉加载更多";
				},1000)
				// this.tablist[this.tabIndex].loadtext="没有更多数据了";
			},
			//下拉刷新逻辑
			getdata(){
				setTimeout(()=>{
					//获取数据
					let arr=[
						//文字
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"哈哈哈123",
							sex:0,//0男1女
							age:25,
							isguanzhu:false,
							title:"我是标题353322",
							titlepic:"",
							video:false,
							share:false,
							path:"深圳 龙岗123",
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
						}
					];
					//赋值
					this.tablist[this.tabIndex].list=arr;
					//关闭下拉刷新
					uni.stopPullDownRefresh();
				}, 2000);
			}
		}
	}

</script>

<style>

</style>

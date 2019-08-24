<template>
	<view>
		<template v-if="list.length>0">
			<block v-for="(item,index) in list" :key="index">
				<index-list :item="item" :index="index"></index-list>
			</block>
			<!-- 上拉加载更多 -->
			<load-more :loadtext="loadtext"></load-more>
		</template>
		
		<template v-else-if="issearch && list.length<1">
			<!-- 无内容列表 -->
			<no-thing></no-thing>
		</template>				
	</view>
</template>

<script>
	import indexList from "../../components/index/index-list.vue";
	import noThing from '../../components/common/no-thing.vue';
	import loadMore from '../../components/common/load-more.vue';
	export default {
		components:{
			indexList,
			noThing,
			loadMore
		},
		data() {
			return {
				issearch:false,
				loadtext:"上拉加载更多",
				list:[],
				searchtetx:""
			}
		},
		//监听原生标题导航按钮点击事件(取消按钮)
		onNavigationBarButtonTap(e){
			console.log(JSON.stringify(e));
			if(e.index==0){
				uni.navigateBack({
					delta:1
				})
			}
		},
		//监听搜索框文本变化
		onNavigationBarSearchInputChanged(e){
			console.log("监听搜索框文本变化"+JSON.stringify(e));
			console.log(e.text);
			// if(e.text){
			// 	this.getdata(e.text)
			// }
			this.searchtext=e.text;
		},
		//监听点击搜索按钮事件
		onNavigationBarSearchInputConfirmed(e){
			// console.log("监听点击搜索按钮事件"+JSON.stringify(e));
			console.log(e.text);
			if(e.text){
				this.getdata();
			}
		},
		//监听上拉触底事件
		onReachBottom() {
			this.loadmore();
		},
		//监听下拉刷新
		onPullDownRefresh() {
			this.getdata()
			uni.stopPullDownRefresh();
		},
		methods: {
			//搜索事件
			getdata(){
				uni.showLoading();
				//请求服务器 post keyword:val
				setTimeout(()=>{
					let arr=[
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"昵称",
							isguanzhu:true,
							title:"我是标题",
							type:"video",//img图文 video视频
							titlepic:"../../static/demo/datapic/11.jpg",//封面图
							playnum:"20w",
							long:"2:47",
							infonum:{
								index:1,//0没有操作  1已经顶了 2已经踩了
								dingnum:11,
								cainum:11
							},
							commentnum:10,//评论
							sharenum:10
						},
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"昵称",
							isguanzhu:true,
							title:"我是标题",
							type:"video",//img图文 video视频
							titlepic:"../../static/demo/datapic/11.jpg",//封面图
							playnum:"20w",
							long:"2:47",
							infonum:{
								index:1,//0没有操作  1已经顶了 2已经踩了
								dingnum:11,
								cainum:11
							},
							commentnum:10,//评论
							sharenum:10
						}
					]
					this.list=arr;
					this.issearch=true;
				},1000)
				uni.hideLoading();
			},
			//上拉加载
			loadmore(){
				if(this.loadtext!="上拉加载更多"){
					return;
				}
				//修改状态
				this.loadtext="加载中...";
				setTimeout(()=>{
					let obj={
						userpic:"../../static/demo/userpic/12.jpg",
						username:"昵称",
						isguanzhu:false,
						title:"我是标题",
						type:"img",//img图文 video视频
						titlepic:"../../static/demo/datapic/11.jpg",//封面图
						infonum:{
							index:0,//0没有操作  1已经顶了 2已经踩了
							dingnum:11,
							cainum:11
						},
						commentnum:10,//评论
						sharenum:10
					};
					this.list.push(obj);
					this.loadtext="上拉加载更多";
				},2000)
				
			}
		}
	}
</script>

<style>

</style>
 
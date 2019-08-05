<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="back"  @click-left="back" class="u-f-ajc">
			<view class="u-f-ajc">
				所有人可见
				<view clas="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from '@/components/uni-nav-bar/uni-nav-bar.vue';
	export default {
		components:{
			uniNavBar
		},
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>

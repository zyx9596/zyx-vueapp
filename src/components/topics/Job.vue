<template>
  <div class="job">
    <!-- 栏目列表 -->
		<topic-list :items="items"></topic-list>
		<!-- 滑动组件模块 -->
		<infinite-loading @infinite="infiniteHandler" class="juhua" v-if="items.length"></infinite-loading>
  </div>
</template>

<script>
// 引入滑动组件
import InfiniteLoading from 'vue-infinite-loading';
// 引入获取栏目数据的模块
import { getItemList } from "@/getdata/getTopic.js";
// 引入 栏目列表的组件
import TopicList from "@/components/topics/TopicList"

export default {
  name: "Job",
  data() {
    return {
			// 栏目列表
			items:[],
			// 默认第一页数据
			page:1
    };
	},
	
	// 加载组件
	components:{
		// 栏目列表
		TopicList,
		// 滑动组件
		InfiniteLoading
	},

	// 钩子函数
  mounted: function () {
    // 查询 招聘 的数据列表
		getItemList({tab:'job'}).then((data)=>{
      this.items = data.data.data;
		})
	},
	// 方法
	methods: {
    infiniteHandler($state) {
      setTimeout(() => {
				// 请求下一页数据
				getItemList({tab:'job',limit:20,page:++this.page}).then((data)=>{
					// 把下一页的数据 追加到 items 数组里
					this.items = this.items.concat(data.data.data);
					// 重新 调用函数
					$state.loaded();

				})
			}, 1000);
    }
  }
};
</script>
<style lang="scss">
  // 引入样式表重置
	@import '../../assets/sass/base.scss';
	.juhua{
		margin-bottom: rem(100px);
	}
</style>
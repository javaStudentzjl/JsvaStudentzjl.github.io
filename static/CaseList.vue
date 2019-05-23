<template>
<div class="caselist">
   <mescroll-vue ref="mescroll" :down="mescrollDown" :up="mescrollUp" @init="mescrollInit">
    <div>
     <ul>
     <router-link :to="'/CaseContent/'+ item.id" tag="li"  v-for="item in dataList" class="item" :key="item.id" >
        <div  class="item-bg">
         <div class="item-h">
          <h2 class="name" v-html="item.title"></h2>
         </div>
         <div  class="icon">
            <img :src="item.picUrl" class="icon-img">
         </div>
         <div class="mate">
           <span v-html="item.ctime" class="time"></span>
           <span v-html="item.source" class="source"></span>
         </div>
        </div>
      </router-link>
      </ul>
    </div>
   </mescroll-vue>
 </div>
</template>

<script>
import MescrollVue from 'mescroll.js/mescroll.vue'
export default {
  name: 'CaseList',
  components: {
       MescrollVue
  },
  data () {
          return {
            dataList: [], // 列表数据
            mescroll: null, // mescroll实例对象
            mescrollDown: {
               auto: false, // 是否在初始化完毕之后自动执行下拉回调callback; 默认true
               callback: this.downCallback
			},
            mescrollUp: {
              callback: this.upCallback, // 上拉回调,此处可简写; 相当于 callback: function (page, mescroll) { getListData(page); }
              page: {
                 num: 0, // 当前页码,默认0,回调之前会加1,即callback(page)会从1开始
                 size: 10 // 每页数据的数量
			  },
			  htmlNodata: '<p class="upwarp-nodata">-- END --</p>',
             noMoreSize: 5, // 如果列表已无数据,可设置列表的总数量要大于等于5条才显示无更多数据;避免列表数据过少(比如只有一条数据),显示无更多数据会不好看

             },
             lazyLoad: {
              use: true // 是否开启懒加载,默认false
            }
           }

          },

        methods: {
          // mescroll组件初始化的回调,可获取到mescroll对象
          mescrollInit (mescroll) {
            this.mescroll = mescroll  // 如果this.mescroll对象没有使用到,则mescrollInit可以不用配置
          },
          // 上拉回调 page = {num:1, size:10}; num:当前页 ,默认从1开始; size:每页数据条数,默认10
         upCallback (page, mescroll) {
			      // 联网请求
			      this.$axios.get('http://api.tianapi.com/meinv/?&key=cbac1121d0ca1f7d12ac3e3068038a84&num=8', {
			        params: {
			          num: page.num, // 页码
			          size: page.size // 每页长度
			        }
			      }).then((response) => {
			        // 请求的列表数据
			        let arr = response.data;
                    let ndata = arr.newslist;
			        //如果是第一页需手动制空列表
			        if (page.num == 1) this.dataList = [];
			        //把请求到的数据添加到列表
			        this.dataList = this.dataList.concat(ndata);
			        //数据渲染成功后,隐藏下拉刷新的状态
			        this.$nextTick(() => {
			          this.mescroll.endSuccess(arr.length);
			        })
			      }).catch((e) => {
			        // 联网失败的回调,隐藏下拉刷新和上拉加载的状态;
			        mescroll.endErr()
			      })
			    }
			  }



}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus"  scoped>
.mescroll
     position: fixed
     top: 44px
     bottom: 0
     height: auto
    .item
       background-color: #f5f5f5
       width: 100%
       height: 0
       overflow: hidden
       padding-bottom: 79%
      .item-bg
        background-color: #ffffff
        width: 100%
        height: 0
        overflow: hidden
        padding-bottom: 76%
       .item-h
          background-color: #ffffff
          width: 100%
          height: 0
          overflow: hidden
          padding-bottom: 11%
          border-bottom-style:solid
          border-color:#f5f5f5
          border-width:2px
          .name
             float: left
             padding:15px 0px 10px 8px
             font-size:13px
             font-family: sans-serif
             font-style:normal
             font-weight:600
        .icon
            background-color: #ffffff
            width: 100%
            height: 0
            overflow: hidden
            padding-bottom: 55%
           .icon-img
             padding:5px 10px 0px 10px
             width:100%
             height:auto
             overflow: hidden
        .mate
          .time
             float: right
             padding: 15px 10px 10px 0px
          .source
             float: left
             padding: 15px 0px 10px 10px






</style>


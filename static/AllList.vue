<template>
  <div class="caselist">
    <ul>
        <li class="item"  v-for="item in dataList" :key="item.id">
         <div class="item.h">
          <router-link :to="'/NewsContent/'+ item.id">
            <h2 class="title" v-html="item.title"></h2>
            <p  class="desc" v-html="item.desc"></p>
          </router-link>
         </div>
         <div class="mate">
           <span v-html="item.source" class="source"></span>
           <span v-html="item.ctime" class="time"></span>
           <router-link tag="span" to=" " class="delete">删除</router-link>
           <router-link tag="span" to=" " class="alter">修改</router-link>
         </div>

        </li>
    </ul>


 </div>
</template>



<script>
import MescrollVue from 'mescroll.js/mescroll.vue'
export default {
  name: 'AllList',
  components: {
       MescrollVue
  },
  data () {
          return {
            dataList: [
				{
					title: '日本90后画家画鱼',
					desc: '人们常说一句话，那就是“鱼儿离不开水”。可是，小编告诉大家日本有这么一位90后画家画鱼，那水平堪比冷军。他画画的技巧，就很有特色。他没有画水，却画出了鱼儿游动的感觉',
					ctime: '时间',
					source: '来源'
				},
				{
					title: '日本90后画家画鱼',
					desc: '人们常说一句话，那就是“鱼儿离不开水”。可是，小编告诉大家日本有这么一位90后画家画鱼，那水平堪比冷军。他画画的技巧，就很有特色。他没有画水，却画出了鱼儿游动的感觉',
					ctime: '时间',
					source: '来源'
				}
			]
		  }

  },

  methods: {


  }



}
</script>

<style lang="stylus"  scoped>
   .item
     background-color: #ffffff
     width: 100%
     height: 0
     overflow: hidden
     padding-bottom: 35%

     .item-h
       background-color: #ffffff
       width: 100%
       height: 0
       overflow: hidden
       padding-bottom: 27%
       border-bottom-style:solid
       border-color:#f5f5f5
       border-width:2px
	   .title
        padding: 8px 10px 5px 10px
        font-size:13px
        font-family: sans-serif
        font-style:normal
        font-weight:550
        line-height: 150%
      .desc
        padding: 8px 10px 5px 10px
        font-size:12px
        font-family: sans-serif
        font-style:normal
        font-weight:normal
        line-height: 150%
     .mate
        .time
           float: left
           padding: 8px 10px 10px 10px
        .source
           float: left
           padding: 8px 10px 10px 10px
        .alter
           float: right
           padding: 8px 7px 10px 0px
        .delete
           float: right
           padding: 8px 7px 10px 0px











</style>

<template>
<div class="caselist">
  <scroller style="top: 0px;"
      :on-refresh="refresh"
      :on-infinite="infinite"
      refresh-layer-color="#4b8bf4"
      loading-layer-color="#ec4949"
    >
      <!-- custom refresh spinner, use default `spinner` & viewBox 0,0,64,64 class -->
      <svg class="spinner" style="stroke: #4b8bf4;" slot="refresh-spinner" viewBox="0 0 64 64">
        <g stroke-width="7" stroke-linecap="round"><line x1="10" x2="10" y1="27.3836" y2="36.4931"><animate attributeName="y1" dur="750ms" values="16;18;28;18;16;16"
        repeatCount="indefinite"></animate><animate attributeName="y2" dur="750ms" values="48;46;36;44;48;48" repeatCount="indefinite"></animate><animate
        attributeName="stroke-opacity" dur="750ms" values="1;.4;.5;.8;1;1" repeatCount="indefinite"></animate></line><line x1="24" x2="24" y1="18.6164"
        y2="45.3836"><animate attributeName="y1" dur="750ms" values="16;16;18;28;18;16" repeatCount="indefinite"></animate><animate attributeName="y2" dur="750ms"
        values="48;48;46;36;44;48" repeatCount="indefinite"></animate><animate attributeName="stroke-opacity" dur="750ms" values="1;1;.4;.5;.8;1"
        repeatCount="indefinite"></animate></line><line x1="38" x2="38" y1="16.1233" y2="47.8767"><animate attributeName="y1" dur="750ms" values="18;16;16;18;28;18"
        repeatCount="indefinite"></animate><animate attributeName="y2" dur="750ms" values="44;48;48;46;36;44" repeatCount="indefinite"></animate><animate
        attributeName="stroke-opacity" dur="750ms" values=".8;1;1;.4;.5;.8" repeatCount="indefinite"></animate></line><line x1="52" x2="52" y1="16" y2="48"><animate
        attributeName="y1" dur="750ms" values="28;18;16;16;18;28" repeatCount="indefinite"></animate><animate attributeName="y2" dur="750ms" values="36;44;48;48;46;36"
        repeatCount="indefinite"></animate><animate attributeName="stroke-opacity" dur="750ms" values=".5;.8;1;1;.4;.5" repeatCount="indefinite"></animate></line></g></svg>

    <div>
     <ul>
     <router-link :to="'/CaseContent/'+ item.id" tag="li"  v-for="item in items" class="item" :key="item.id" >
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
   <svg class="spinner" style="fill: #ec4949;" slot="infinite-spinner" viewBox="0 0 64 64">
        <g><circle cx="16" cy="32" stroke-width="0" r="3"><animate attributeName="fill-opacity" dur="750ms" values=".5;.6;.8;1;.8;.6;.5;.5"
        repeatCount="indefinite"></animate><animate attributeName="r" dur="750ms" values="3;3;4;5;6;5;4;3" repeatCount="indefinite"></animate></circle><circle cx="32"
        cy="32" stroke-width="0" r="3.09351"><animate attributeName="fill-opacity" dur="750ms" values=".5;.5;.6;.8;1;.8;.6;.5" repeatCount="indefinite"></animate><animate
        attributeName="r" dur="750ms" values="4;3;3;4;5;6;5;4" repeatCount="indefinite"></animate></circle><circle cx="48" cy="32" stroke-width="0" r="4.09351"><animate
        attributeName="fill-opacity" dur="750ms" values=".6;.5;.5;.6;.8;1;.8;.6" repeatCount="indefinite"></animate><animate attributeName="r" dur="750ms"
        values="5;4;3;3;4;5;6;5" repeatCount="indefinite"></animate></circle></g></svg>
  </scroller>
 </div>
</template>

<script>
  export default {
    name:'CaseList',
    components: {

    },
    data () {
      return {
         items: []
      }
    },
    mounted() {



    },
    methods: {

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus"  scoped>
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


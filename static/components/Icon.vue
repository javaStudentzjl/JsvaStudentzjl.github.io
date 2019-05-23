<template>
  <div class="icons">
  <div class="icon-con">
     <div class="icon">
        <button>
          <router-link to="/home">
            <div class="icon-img">
              <img class="img-con" src="@/common/fonts/zhaoxiangji.png" >
            </div>
            <p class="icon-desc">交警家访</p>
          </router-link>
        </button>
     </div>

  </div>
  </div>
</template>

<script>
import { XButton } from 'vux'
export default {
  name: 'HomeIcon',
  components: {
    XButton
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
   .icons
    background-color: #f5f5f5
    width: 100%
    height: 0
    overflow: hidden
    padding-bottom: 97%
    .icon-con
     background-color: #ffffff
     width: 100%
     height: 0
     overflow: hidden
     padding-bottom: 84%
    .icon
      position: relative
      float: left
      width: 50%
      height: 0
      overflow: hidden
      padding-bottom: 20%
      icon-button
       color:red
      .icon-img
        position: absolute
        top: 0
        left: 0
        right: 0
        bottom: .44rem
        box-sizing: border-box
        padding: .1rem
        .img-con
          display: block
          margin: 0 auto
          height: 100%
      .icon-desc
           position: absolute
           left: 0
           right: 0
           bottom: 0
           height: 0.85rem
           line-height: 0.85rem
           text-align: center
           color #333
</style>

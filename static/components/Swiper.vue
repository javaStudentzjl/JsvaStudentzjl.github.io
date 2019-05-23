<template>
<div>
  <swiper :options="swiperOption">
    <!-- slides -->
    <swiper-slide>
      <div class="wapper">
        <img class="swiper-img" src="@/common/images/01.jpg">
      </div>
    </swiper-slide>
    <swiper-slide>
       <div class="wapper">
        <img class="swiper-img" src="@/common/images/02.jpg">
      </div>
    </swiper-slide>
    <swiper-slide>
       <div class="wapper">
        <img class="swiper-img" src="@/common/images/03.jpg">
      </div>
    </swiper-slide>

    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
</div>
</template>

<script>
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  name: 'Swiper',
  components: {
    swiper,
    swiperSlide
  },
  data () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        },
        notNextTick: true,
        autoplay: {
          delay: 3500,
          disableOnInteraction: false
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="stylus" scoped>
    .wapper
      width:100%
      height:0
      overflow hidden
      padding-bottom: 55%
      .swiper-img
         width: 100%

</style>

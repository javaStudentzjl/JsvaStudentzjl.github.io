<template>
  <div class="header">
     <x-header :left-options="{showBack:''}" title="恩施州交通管理应用平台" style="background-color:#35495e;">

     </x-header>
  </div>
</template>

<script>
import { XHeader } from 'vux'
export default {
  name: 'Header',
  components: {
    XHeader
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >

</style>

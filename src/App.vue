<template>
  <div id="">
    <v-header :seller="seller"></v-header>
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link> 
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link> 
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link> 
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script type="text/ecmascript-6">
  import header from "./components/header/header";
  const ERR_OK = 0;
  export default {
    data(){
      return {
        seller:{}
      } 
    },
    created() {
      this.$http.get('/api/seller').then((response) =>{
        response = response.body;
        if(response.errno === ERR_OK){
          this.seller = response.data;
        }
      })
    },
    components: {
      "v-header": header
    }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
.tab
  .tab-item
    display inline-block
    font-size .24rem
</style>

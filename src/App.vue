<template>
  <div id="">
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
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
    <keep-alive>
      <router-view :seller="seller"></router-view>
    </keep-alive>
  </div>
</template>

<script type="text/ecmascript-6">
import header from "./components/header/header";
const ERR_OK = 0;
export default {
  data() {
    return {
      seller: {}
    };
  },
  created() {
    this.$http.get("/api/seller").then(response => {
      response = response.body;
      if (response.errno === ERR_OK) {
        this.seller = response.data;
      }
    });
  },
  components: {
    "v-header": header
  }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
@import 'common/stylus/mixin.styl';

/* 三等分flex布局 */
.tab {
	display: flex;
	width: 100%;
	height: 0.8rem;
	line-height: 0.8rem;
	border-1px(rgba(7, 17, 27, 0.1));
}

.tab-item {
	flex: 1;
	display: block;
	text-align: center;
	font-size: 0.28rem;
	color: rgb(77, 85, 93);
}

.tab-item .active {
	color: rgb(240, 20, 20);
}
</style>

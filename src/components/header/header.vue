<template>
    <div class="header">
        <div class="content-wrap">
            <div class="avatar">
                <img class="avatarimg" :src="seller.avatar" alt="">
            </div>
            <div class="content">
                <div class="title">
                    <i class="brand"></i>
                    <span class="name">{{seller.name}}</span>
                </div>
                <div class="desc">
                    {{seller.description}} / {{seller.deliveryTime}}分钟送达
                </div>
                <div v-if="seller.supports" class="support">
                    <i class="brand" :class="classMap[seller.supports[0].type]"></i>
                    <span class="text">{{seller.supports[0].description}}</span>
                </div>
                <div v-if="seller.supports" class="supports-count" @click="showDetail">
                    <span class="count">{{seller.supports.length}}个</span>
                    <i class="arrowright iconfont icon-zuoyoujiantou"></i>
                </div>    
            </div>
        </div>
        <div class="bulletin-wrapper" @click="showDetail">
            <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
            <i class="icon iconfont icon-zuoyoujiantou"></i>
        </div>     
        <div class="background">
            <img :src="seller.avatar" alt="">    
        </div>
        <div v-show="isShow" class="detail" @click="hideDetail">
            <div class="detail-wrap clearfix">
                <div class="detail-main">
                    <h1 class="name">{{seller.name}}</h1>
                    <div class="star-wrap">
                        <star :size = "48" :score = "seller.score"></star>
                    </div>
                    <div class="title">
                        <div class="line"></div>
                        <div class="text">优惠消息</div>
                        <div class="line"></div>
                    </div>
                    <ul v-if="seller.supports" class="supports">
                        <div class="supports">
                            <li class="support-item" v-for = "(item,index) in seller.supports">
                                <span class="icon" :class="classMap[seller.supports[index].type]"></span>
                                <span class="text">{{seller.supports[index].description}}</span>
                            </li>
                        </div>
                    </ul>
                    <div class="title">
                        <div class="line"></div>
                        <div class="text">商家公告</div>
                        <div class="line"></div>
                    </div>
                    <div class="bulletin">
                        <p class="content">{{seller.bulletin}}</p>
                    </div>
                </div>
            </div>
            <div class="detail-close" @click="hideDetail">
                <i class="iconfont icon-cha"></i>
            </div>
        </div>
    </div>
</template>

<script type="text/ecmascript-6">
import star from '../star/star'
export default {
    props:{
        seller:{
            type:Object,
        }
    },
    components:{
        star
    },
    data(){
        return {
            isShow:false,
            classMap:['decrease', 'discount', 'special', 'invoice', 'guarantee']
        }    
    },
    methods:{
        showDetail(){
            this.isShow = true
        },
        hideDetail(){
            this.isShow = false
        }
    }
};
</script>

<style lang="stylus" rel="stylesheet/stylus">
    @import "header.styl"
</style>

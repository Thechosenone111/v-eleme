<template>
    <transition name="fade">
    <div class="food" v-show="showFlag">
        <div class="food-content">
            <div class="image-header">
                <img :src="food.image" alt="">
                <div class="back" @click="hide">
                    <i class="iconfont icon-weibiaoti6-copy"></i>
                </div>
            </div>
            
        </div>
    </div>
    </transition>
</template>
<script text="text/ecmascript-6">

export default {
    props: {
        food: {
            type: Object
        }
    },
    data() {
        return {
            showFlag: false
        }
    },
    methods: {
        show() {
            this.showFlag = true
        },
        hide() {
            this.showFlag = false
        }
    }
}
</script>

<style lang="stylus" type="stylesheet/stylus">
    @import "food.styl";
</style>

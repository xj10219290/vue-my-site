<template>
  <i class="iconfont icon-container" :class="iconType"></i>
</template>

<script>
const iconMap= {
    home:'icon-iconfonticonzhuye'
}
export default {
    props: {
        type: {
            type: String,
            required: true
        }
    },
    computed: {
        iconType(){
            return iconMap[this.type]
        }
    }
}
</script>

<style scoped>
    /* @import '//at.alicdn.com/t/c/font_4931503_inmt03vm8ms.css'; */
   

    .iconfont {
        color: #f00;
        font-size: 30px;
    }
</style>
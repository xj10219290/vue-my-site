<template>
    <!--总页数大于1时在显示-->
  <div class="pager-container" v-if="pageNumber > 1">
    <a :class="{disabled: current === 1}" @click="clickHandler(1)">|&lt;&lt;</a>
    <a :class="{disabled: current === 1}" @click="clickHandler(current - 1)">&lt;&lt;</a>
    <!-- <a class="active">1</a>
    <a>2</a>
    <a>3</a>
    <a>4</a>
    <a>5</a>
    <a>6</a> -->
    <a v-for="(n, i) in numbers" :key="i" :class="{active: n === current}" @click="clickHandler(n)">{{n}}</a>
    <a :class="{disabled: current === pageNumber}"  @click="clickHandler(current + 1)">&gt;&gt;</a>
    <a :class="{disabled: current === pageNumber}"  @click="clickHandler(pageNumber)">&gt;&gt;|</a>
  </div>
</template>

<script>
export default {
    methods: {
        clickHandler(newPage){
            if(newPage > this.pageNumber) {
                newPage = this.pageNumber
            }

            if(newPage < 1) {
                newPage = 1
            }
            this.$emit('pageChange', newPage)
        }
    },
    props: {
        current:{// 当前第几页
            default: 1,
            type: Number
        },
        total: { // 总的数据量
            type: Number,
            default: 0
        },
        limit: {//页容量，每页有多少数据
            type: Number,
            default: 10
        },
        visableNumber: {
            type: Number,
            default: 10
        }
    },
    data(){
        return{

        }
    },
    computed: {
        pageNumber(){
            return Math.ceil(this.total / this.limit)
        },
        
        //得到页码最小数字
        visibleMin(){
            let min = this.current - Math.floor(this.visableNumber / 2)
            if(min < 1) {
                min = 1
            }
            return min
        },
        visibleMax(){
            let max = this.visibleMin + this.visableNumber -1
            if(max > this.pageNumber) {
                max = this.pageNumber
            }
            return max
        },
        numbers(){
            const arr = []
            for(let i = this.visibleMin;i <= this.visibleMax;i++ ) {
                arr.push(i)
            }
            return arr
        },
    }
}
</script>

<style lang="less" scoped>
@import '~@/styles/var.less';
 .pager-container {
    display: flex;
    justify-self: center;
    margin: 20px 0;
 }
 a {
    color: @primary;
    cursor: pointer;
    margin: 0 6px;
    &.disabled{
        color: @lightWords;
        cursor: not-allowed;
    }
    &.active {
        color: @words;
        font-weight: bolder;
    }
 }
</style>
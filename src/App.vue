<template>
  <div>
    <h1>App组件</h1>
    <Icon :type="'home'" />
    <Avatar url="/hsq.png" :size="50"  />
    <Pager :current="current" :total="300" @pageChange="pageChangeHandler($event)"></Pager>
  </div>
</template>

<script>
import Avatar from './components/Avatar.vue'
import Icon from './components/Icon.vue'
import Pager from './components/Pager.vue';

export default {
  components: {
    Avatar,
    Icon,
    Pager
  },
  data(){
    return {
      current: 1
    }
  },
  methods: {
    pageChangeHandler($event){
      console.log($event);
      this.current = $event
    }
  }
}
</script>
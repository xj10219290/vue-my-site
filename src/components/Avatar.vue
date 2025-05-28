<template>
  <img class="avatar-container" :src="url" alt=""  :style="{width: size + 'px', height: size + 'px'}">
</template>

<script>
export default {
    props:['url', 'size']
}
</script>

<style scoped>
    .avatar-container {
        /* border: 1px solid #000; */
        border-radius: 50%;
        display: block;
    }
</style>
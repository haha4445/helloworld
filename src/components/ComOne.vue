<template>
  <div>
    <!-- 自定义组件的v-model  https://cn.vuejs.org/v2/guide/components-custom-events.html -->
    <input type="checkbox" :checked="checked" @change="$emit('change',$event.target.checked)">
  </div>
</template>

<script>
  export default {
    model:{
      prop:'checked',
      event:'change'
    },
    props:{
      checked:Boolean
    }
  }
</script>

<style lang="scss" scoped>

</style>
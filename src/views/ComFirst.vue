<template>
  <div>
    {{loginVue}}
    <com-one v-model="loginVue"></com-one>
    <com-two v-model="uname" :label="'基础输入组件'" @focus="handleFocus"></com-two>
  </div>
</template>

<script>
import ComOne from '@/components/ComOne.vue'
import ComTwo from '@/components/ComTwo.vue'
  export default {
  components: { ComOne, ComTwo },
  data() {
    return {
      loginVue: true,
      uname:''
    }
  },
  methods: {
    handleFocus(e) {
      console.log(e)
    }
  },
  beforeUpdate () {
    console.log(this.uname);
  },    
  }
</script>

<style lang="scss" scoped>

</style>
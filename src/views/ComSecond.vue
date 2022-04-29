
<template>
<!-- 纯前端验证码验证，5种方法 -->
      <Verify @success="verifyStatus='success'" @error="verifyStatus='error'" :type="4"></Verify>
</template>


<script>
    import Verify from 'vue2-verify'

    export default {
        name: 'app',
        methods: {
            alert(text) {
                console.log(text)
            }
        },
        components: {
            Verify
        },
        data() {
          return {
            verifyStatus: 'error'
          }
        },
    }
</script>
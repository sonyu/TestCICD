<template>
  <div id="app">
    <!-- Hiển thị nội dung chào mừng từ Vue.js -->
    {{ message }}
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      message: 'Hello World! I am here !'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
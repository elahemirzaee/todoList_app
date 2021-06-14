<template>
  <header class="header">
    <h1>TodoList</h1>
    <router-link to="/"><span>Home</span></router-link> |
    <router-link to="/about"><span>About</span></router-link>
  </header>
</template>
<script>
export default {
  name: 'TheHeader'
}
</script>
<style scoped>
.header {
  background: #333;
  color: #fff;
  text-align: center;
  padding: 10px;
}
.header a {
  color: #fff;
  padding-right: 5px;
  text-decoration: none;
}
span {
  color: #fff;
}
</style>
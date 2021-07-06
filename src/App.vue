<template>
  <h1>Simple vue form</h1>
  <Form />
</template>

<script>
import Form from './components/Form.vue'
export default {
  components: { Form },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  height: 100vh;
  width: 100vw;
}
body{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>

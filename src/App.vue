<template>
  <div id="app">
    <textInput 
      placeholder="Enter my placeholder text" 
      initialValue=""
      :customStyle="{borderRadius: '4px'}"
    />
  </div>
</template>

<script>
import textInput from './components/textInput.vue'

export default {
  name: 'app',
  components: {
    textInput
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

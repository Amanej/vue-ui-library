<template>
  <div id="app">
    <div class="container"> <!-- Container -->
      <textInput 
        placeholder="Enter my placeholder text" 
        initialValue=""
        :customStyle="{borderRadius: '4px'}"
      />
    </div>
    <div class="container"> <!-- Container -->
      <selectInput />
    </div>
    <div class="container"> <!-- Container -->
      <selectInput :withInput="true" />
    </div>
  </div>
</template>

<script>
import textInput from './components/textInput.vue'
import selectInput from './components/selectInput.vue'

export default {
  name: 'app',
  components: {
    textInput,
    selectInput
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
div.container {
      margin: 20px auto;
      width: 250px;
}
</style>

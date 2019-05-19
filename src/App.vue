<template>
  <div id="app">
    <div class="container"> <!-- Container -->
      <textInput 
        placeholder="Enter my placeholder text" 
        initialValue=""
        :customStyle="firstTextInputStyle"
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
import textInput from './components/Text/TextInput'
import selectInput from './components/Select/SelectInput'

const firstTextInputStyle = {
  input: {
    borderRadius: '4px'
  },
  label: {}
};

const secondTextInputStyle = {
  input: {
    borderRadius: '4px'
  },
  label: {
    marginTop: '4px'
  }
};

export default {
  name: 'app',
  components: {
    textInput,
    selectInput
  },
  computed: {
    firstTextInputStyle() {
      return firstTextInputStyle
    },
    secondTextInputStyle() {
      return secondTextInputStyle
    }
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

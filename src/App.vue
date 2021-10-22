<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div class="box">
        <p><strong>Basic Example {{ test }}</strong></p>
        <ToggleButton v-model="test" @input="handleChange" />
    </div>
  </div>
</template>


<script>
import ToggleButton from './components/ToggleButton.vue'


export default {
  name: 'App',
  components: {
    ToggleButton
  },
  data(){
      return {
        test: true
      }
  },
  methods: {
    handleChange: function(val){
      return this.test = val
    }
  }
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
}

.box {
    text-align:center;
    margin-bottom: 30px;
}
</style>

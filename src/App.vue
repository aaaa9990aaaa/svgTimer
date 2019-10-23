<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <div class="center">
      <timer-chart :options="options" />
      <wd-input v-model="options.num" />
    </div>
  </div>
</template>

<script>
import timerChart from './components/timerChart'
import wdInput from './components/input'
export default {
  name: 'App',
  components: {
    timerChart, wdInput
  },
  data() {
    return {
      options: {
        total: 100,
        num: 50,
        company:'单位'
      }
    }
  }
}
</script>

<style lang="scss">
@import './components/font/font.css';
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
  .center{
    width: 15rem;
    height: 25rem;
    .chart {
      margin-bottom: 2rem;
    }
  }
}
html {
   background: #000;
   
}
</style>

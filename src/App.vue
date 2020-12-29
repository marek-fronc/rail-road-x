<template>
<cross-light :train="train" class='cross-light-table'/>
  <div class="rod"></div>
  <button @click="train= !train" class="switch">Train: {{train}}</button>
</template>

<script>
import CrossLight from './components/CrossLight.vue'

export default {
  name: 'App',
  components: {
    CrossLight
  },
  data(){
    return{
      train: false
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
  margin-top: 0;
}
.cross-light-table{
  max-height: 60vh;
  max-width: 60vw;
  margin: 0 auto;
  z-index: 10;
  position: relative;
  box-shadow: 10px 10px 100px #333;
}
.rod{
  z-index: 1;
  position: absolute;
  top: 66vmin;
  left: calc(50% - 2.5vmin);
  border-radius: 5vmin/2.5vmin;
  width: 5vmin;
  height: 30vh;
  background: radial-gradient(2.5vmin 1.25vmin ellipse at 50% 1.25vmin, grey 95%, transparent 100%, transparent),
    linear-gradient(to right, grey, #666, grey);
}
.switch{
  position: fixed;
  bottom: 0;
  right: 0;
  padding: 20px;
  font-size: 3em;
}
@keyframes singleblink{
  0%{ opacity: 1}
  50%{
    opacity: 0.3}
  100%{
    opacity: 1;
  }
}
</style>

<template>
  <div class="cross-light__wrapper">
  <div class="cross-light">
    <div class="row">
      <light :active="!open" active-color="darkred" passive-color="brown"/>
      <light inverted :active="!open" active-color="darkred" passive-color="brown"/>
    </div>
    <div class="row">
  <light color="blue" :active="open" active-color="darkblue" passive-color="white"/>
    </div>
  </div>
  </div>
</template>

<script>
import Light from './Light.vue'
export default {
  name: 'CrossLight',
  components: {
    Light
  },
  props: {
    time: {type: Number,
    default: 20},
    train:{
      type: Boolean,
      default: false
    }
  },
  data(){
    return{
      count: 20
    }
  },
  mounted(){
    this.count=this.time
  },
  computed:{
    open(){
      if (!this.train) return true
      return false
    },
    // count(){
    //   let count = null
    //   if (this.time > 0) count=this.time
    //   return count
    // },
    even(){
      if( this.count%2===0) return true
      return false
    }
  },
  methods:{
    switch(){
      // let count = this.time
      let val = false
      for (let index = 0; index < this.count; index++) {
        setTimeout(this.minus(this.count), 1000)
        console.log(this.count, val)
        if(this.count===0) val=true
      }
      return val
    },
    minus(val){
      if (val >=1)
        val=val - 1
      return val
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
.row
 display: inline-flex
 justify-content: center
 flex-wrap: wrap
 width: 100%
.cross-light
  background: #000
  width: 100%
  height: 100%
  border-radius: 5vh
.cross-light__wrapper
  border-radius: 5vh

  border: 5vh solid #fff
.light__lamp
  width: 90%
  height: 90%
  border-radius: 50%

.trafficlight
  background: #222
  background-image: linear-gradient(transparent 2%, #111 2%, transparent 3%, #111 30%)
  width: 170px
  height: 400px
  border-radius: 20px
  position: relative
  border: solid 5px #333


.trafficlight:before
  background: #222
  background-image: radial-gradient(#444, #000)
  content: ""
  width: 170px
  height: 150px
  margin: 0 auto
  position: absolute
  top: -20px
  margin-left: 0px
  border-radius: 50%
  z-index: -1

.trafficlight:after
  background: #222
  background-image: linear-gradient(-0deg, #777 10%, #ccc 30%, #000)
  content: ""
  width: 50px
  height: 500px
  margin-left: 60px
  position: absolute
  top: 150px
  z-index: -1


</style>

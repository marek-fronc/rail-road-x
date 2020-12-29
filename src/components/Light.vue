<template>
  <div class="light">
    <div :class="['light__lamp']" :style="styles"></div>
  </div>
</template>

<script>
export default {
  name: 'Light',
  props: {
    activeColor: {type:String,
    default: 'red'},
    passiveColor: {type:String,
    default: 'brown'},
    color: String,
    active: {type:
    Boolean,
    default: false},

    inverted: {type:
    Boolean,
    default: false}
  },
  computed:{
    styles(){
      let values=[]
      values.push({backgroundColor:this.activeColor})
      values.push({backgroundImage: `radial-gradient(${this.passiveColor}, transparent )`})
      values.push({backgroundSize: '5px 5px'})
      values.push({borderRadius: '50%'})
      if(this.active)
        if(this.inverted)
          values.push({animation: `4s singleblink 2s infinite`})
        else
          values.push({animation: `4s singleblink infinite`})
      else
        values.push({opacity: '.3'})
      values.push({border: `dotted 2px ${this.activeColor}`})
      values.push({boxShadow: `0 0 20px #111 inset, 0 0 10px ${this.activeColor}`})
      return values
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="sass">
.light
  background: #000
  width: 30vh
  height: 30vh
  min-height: 30vh
  min-width: 30vh
  border-radius: 50%
  display: flex
  justify-content: center
  align-items: center
  & + &
    .light__lamp
      animation-delay: 2s

.light__lamp
  width: 90%
  height: 90%
  border-radius: 50%
</style>

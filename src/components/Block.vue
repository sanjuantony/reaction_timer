<template>
  <div class="block" :style="{top: topPosition, left: leftPosition}" v-if="showBlock" @click="stopTimer">
      Click me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0,
            topPosition: 0,
            leftPosition: 0
            // '--top': this.topPosition + '%',
            // '--left': this.leftPosition + '%'
        }
   },
   mounted() {
       console.log("Component Mounted: "+this.delay)
       setTimeout(()=>{
           this.showBlock = true
           this.startTimer()
       },this.delay)
       this.topPosition = Math.random() * 80 + '%'
       this.leftPosition = Math.random() * 80 + '%'

       console.log("Top Position: "+this.topPosition + ", Left Position: "+this.leftPosition)
   },
   updated() {
       console.log("Component Updated")
   },
   unmounted() {
       console.log("Component Unmounted")
   },
   methods: {
       startTimer() {
        this.timer = setInterval(() => {
            this.reactionTime += 2
        }, 2)
       },
       stopTimer() {
           clearInterval(this.timer)
           console.log("Reaction Time: "+this.reactionTime)
           this.showBlock = false
           this.$emit("endGame", this.reactionTime)
       }
   }
}
</script>

<style>
    .block {
        position: fixed;
        /* top: this.topPosition;
        left: var(--left); */
        width: 150px;
        height: 10px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>
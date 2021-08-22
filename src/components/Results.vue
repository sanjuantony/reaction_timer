<template>
  <p>Reaction Time: {{ reactionTime }} ms</p>
  <p class="rank"> {{ rank }} </p>
</template>

<script>
export default {
    props: ["reactionTime"],
    data() {
      return {
        rank: null
      }
    },
    mounted() {
      console.log("Results Component: Mounted")
      if(this.reactionTime < 200) {
        this.rank = "Ninja Fingers"
      } else if (this.reactionTime < 400) {
        this.rank = "Rapid Reflexes"
      } else {
        this.rank = "Snail Pace"
      }
    }
}
</script>

<style>
  p {
    background-color:floralwhite;
  }
  .rank {
    font-size: 1.4em;
    color: chartreuse;
    font-weight: bold;
  }
</style>
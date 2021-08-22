<template>
  <p>Average Time: {{this.time_received}}</p>
</template>

<script>
export default {
    props: ['reactionTime'],
    data() {
        return {
            time_received: this.reactionTime
        }
    }

}
</script>

<style>

</style>
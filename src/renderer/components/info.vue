<template>
<div class="info">
    <router-link to="/">close Setup</router-link>
    <label for="tomato">
        tomato time length min.
    </label>
    <input type="text" id="tomato" v-model="tomatoLength" v-on:change="changeTomatoLength">
</div>
</template>

<script>
  export default {
    name: 'info',
    data: function () {
      return {
        tomatoLength: localStorage.getItem('timeTrackerTomatoLength') ? localStorage.getItem('timeTrackerTomatoLength') : 20
      }
    },
    methods: {
      changeTomatoLength: function () {
        localStorage.setItem('timeTrackerTomatoLength', this.tomatoLength)
      }
    }
  }
</script>

<style scoped>

</style>

<template>
  <div id="app">
    <Booking />
  </div>
</template>

<script>
import Booking from './views/Booking.vue';

export default {
  name: 'App',
  components: {
    Booking,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  min-height: 100vh;
  padding: 60px;
  background-color: #d7d7d7;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

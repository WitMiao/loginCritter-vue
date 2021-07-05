<template>
  <div id="app">
    <login-critter />
  </div>
</template>

<script>
import LoginCritter from './components/loginCritter.vue';

export default {
  name: 'App',
  components: {
    LoginCritter,
  },
};
</script>
<style>
body {
  background: #00c0ff;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>

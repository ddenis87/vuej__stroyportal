<template>
  <div id="app">
    <main-page></main-page>
  </div>
</template>

<script>
import mainPage from '@/view/main-page';

export default {
  name: 'App',
  components: {
    mainPage,
  }
}
</script>

<style lang="scss">
@font-face {
  font-family: 'Open sans';
  src: url('~@/assets/fonts/OpenSans-Light.ttf');
  font-weight: normal;
}
@font-face {
  font-family: 'Open sans';
  src: url('~@/assets/fonts/OpenSans-Bold.ttf');
  font-weight: bold;
}
#app {
  font-family: 'Open sans';
  color: #708598;

  a { text-decoration: none; color: #708598;}
}
</style>

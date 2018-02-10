<template>
  <div id="app">
    <titlebar></titlebar>
    <router-view></router-view>
    <Player></Player>
  </div>
</template>

<script>
import Player from './components/Player';
import Titlebar from './components/Titlebar';

export default {
  name: 'bast',
  components: {
    Player,
    Titlebar,
  },
};
</script>

<style>

</style>

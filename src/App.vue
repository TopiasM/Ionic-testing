<template>
  <div id="app">
    <ion-app>
      <ion-vue-router/>
      <ion-button id="statusbarBtn" v-if="statusBar" v-on:click="hideStatusbar()" full>hide statusbar</ion-button>
    </ion-app>
  </div>
</template>

<script>
import { Plugins } from '@capacitor/core';

export default {
  name: 'app',
  data: function() {
    return {
      statusBar: true
    }
  },
  created: function() {
    Plugins.Keyboard.addListener('keyboardDidShow', function() {
      this.statusBar = true;
      console.log("a");
    }.bind(this));
  },
  methods: {
    hideStatusbar: function() {
      Plugins.StatusBar.hide();
      this.statusBar = false;
    }
  }
}
</script>

<style>

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ion-content {
  padding-top: 30px !important;
}

ion-tab-bar {
  position: absolute;
  bottom: 0px;
  width: 100%;
}

</style>

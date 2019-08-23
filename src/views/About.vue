<template>
  <div class="ion-page">
   <ion-content> 
      <div class="about">
	<h1>About page</h1>
	<ion-button v-on:click="$router.push('/')">Home</ion-button>
	<ion-button v-on:click="alertTest()" full>Alert</ion-button>
	<br>
	<h6>Geo location</h6>
	lat: {{geoLoc.latitude}}, long: {{geoLoc.longitude}}
	<h6>Device info</h6>
	<div v-for="(info, title) in deviceInfo">
	  <span>{{title}} => {{info}}</span>
	</div>
      </div>
    </ion-content>
  </div>
</template>

<script>
import { Plugins } from '@capacitor/core';

export default {
  name: 'about',
  data: function() {
    return {
      geoLoc: {latitude: "0", longitude: "0"},
      deviceInfo: {}
    }
  },
  async created() {
    let loc = await Plugins.Geolocation.getCurrentPosition();
    this.geoLoc = loc.coords;
    let info = await Plugins.Device.getInfo();
    this.deviceInfo = info;
  },
  methods: {
    async alertTest() {
      await Plugins.Modals.alert({
	title: 'Alert',
	message: 'Native alert'
      });
    }
  }
}
</script>

<template>
  <div class="ion-page">
   <ion-content> 
      <div class="camera">
	<ion-button v-on:click="$router.push('/')">Go back to Home</ion-button>
	<img v-bind:src="img">
      </ion-item>
    </div>
    </ion-content>
  </div>
</template>

<script>
import { Plugins, CameraResultType, CameraSource } from '@capacitor/core';

export default {
  name: 'camera',
  data: function() {
    return {
      img: ""
    }
  },
  async created() {
    const image = await Plugins.Camera.getPhoto({
      quality: 90,	
      allowEditing: false,
      resultType: CameraResultType.Uri,
      cameraSource: CameraSource.Camera
    });

    this.img = image.webPath;
  },
  methods: {
  }
}
</script>

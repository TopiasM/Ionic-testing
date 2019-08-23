<template>
  <div class="ion-page">    
    <ion-header>
      <ion-toolbar>
	 <ion-title>Test app</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content class="ion-padding">
      <h1>Hello {{name}}!</h1>
      <ion-item>
	<ion-label>NAME</ion-label>
	<ion-input :value="name" @input="name = $event.target.value"></ion-input>
      </ion-item>
    </ion-content>
    <ion-tabs>
      <ion-tab-bar>
	<ion-tab-button tab="account">
	  <ion-icon name="person" v-on:click="$router.push('login')"></ion-icon>
	</ion-tab-button>
	<ion-tab-button tab="about" v-on:click="$router.push('about')">
	  <ion-icon name="help"></ion-icon>
	</ion-tab-button>
	<ion-tab-button v-on:click="$router.push('camera')" tab="camera">
	  <ion-icon name="camera"></ion-icon>
	</ion-tab-button>
      </ion-tab-bar>
    </ion-tabs>
  </div>
</template>

<script>
export default {
  name: 'home',
  data: function() {
    return {
      name: "Stranger"
    }
  }
}
</script>

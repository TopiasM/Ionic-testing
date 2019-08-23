<template>
  <div class="ion-page">
   <ion-content> 
      <div class="login">
	<h1>Login</h1>
	<ion-button v-on:click="$router.push('/')">Go back to Home</ion-button>
	<br>
	<ion-item>
	  <ion-label>Email</ion-label>
	  <ion-input type="text" :value="email" @input="email = $event.target.value"></ion-input>
	</ion-item>
	<ion-item>
	  <ion-label>Password</ion-label>
	  <ion-input type="password" :value="passwd" @input="passwd = $event.target.value"></ion-input>
	</ion-item>
	<ion-button v-on:click="login()">Login</ion-button>
      </div>
    </ion-content>
  </div>
</template>

<script>
import { Plugins } from '@capacitor/core';
import axios from 'axios';

export default {
  name: 'login',
  data: function() {
    return {
      email: "",
      passwd: ""
    }
  },
  created: function() {
    
  },
  methods: {
    /*async alertTest() {
      await Plugins.Modals.alert({
	title: 'Alert',
	message: 'Native alert'
      });
    },*/
    login: function() {
      axios.post("https://dev-cb.blackvuecloud.com:443/BCS/user_login.php", {
	email: this.email,
	passwd: this.passwd,
	app_ver: 1,
	time_interval: 0,
	mobile_uuid: 0,
	mobile_name: 0,
	mobile_os_type: 0
      },
      {headers: {
	/*"bcsSignature" : "3AEE4138F331C7C0566DC88A9DABC95750EC1AFBBB3C581585493D191D014A9F",
	"bcsDate" : "20150830T123600Z",
	"bcsToken" : "hH751PfkmHdktlkNUmS8qDaCGZrdXxMbw8qT2oy78dB3jhebz0n6IvnA4C788Cts"*/
      }}).then(function(resp) {
	console.log(resp);
      }.bind(this));
    }
  }
}
</script>

<template>
  <div class="ion-page">
   <ion-content> 
      <div class="login">
	<h1>Login</h1>
	<ion-button v-on:click="$router.push('/')">Home</ion-button>
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
    login: function() {
      axios.post("url", {
	email: this.email,
	passwd: this.passwd,
      },
      {headers: {
      }}).then(function(resp) {
	console.log(resp);
      }.bind(this));
    }
  }
}
</script>

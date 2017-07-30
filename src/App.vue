<template>
  <div id="app" class="container">
    <div class="page-header">
      <h2>Access Point Lists</h2>
    </div>
    <add-form :addAP = "addAP" :newInfo = "newInfo"></add-form>
    <access-point-lists :wifiInfo = "wifiInfo" :editInfo = "editInfo" :edit = "editWifi" :remove = "removeAP" :temp = "tempEdit"></access-point-lists>
  </div>
</template>

<script>
// import Hello from './components/Hello'
import Firebase from 'firebase'

import AccessPointLists from './components/AccessPointLists'
import AddForm from './components/AddForm'

let config = {
  apiKey: 'AIzaSyCq9XSREG-KQz4IZgmmbcSpRYgz4HK-KpQ',
  authDomain: 'wifi-storage.firebaseapp.com',
  databaseURL: 'https://wifi-storage.firebaseio.com',
  storageBucket: 'wifi-storage.appspot.com',
  messagingSenderId: '1062691344683'
}
let app = Firebase.initializeApp(config)
let db = app.database()

let wifiInfoRef = db.ref('wifiInfo')

export default {
  name: 'app',
  firebase: {
    wifiInfo: wifiInfoRef
  },
  data () {
    return {
      newInfo: {
        apname: '',
        ssid: '',
        location: '',
        model: ''
      },
      editInfo: {
        apname: '',
        ssid: '',
        location: '',
        model: ''
      },
      tempEdit: 0
    }
  },
  components: {
    AccessPointLists,
    AddForm
  },
  methods: {
    addAP: function () {
      wifiInfoRef.push(this.newInfo)
      this.newInfo.apname = ''
      this.newInfo.ssid = ''
      this.newInfo.location = ''
      this.newInfo.model = ''
    },
    editWifi: function (wifi) {
      console.log(wifi)
      this.tempEdit = wifi
    },
    removeAP: function (wifi) {
      wifiInfoRef.child(wifi['.key']).remove()
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
</style>

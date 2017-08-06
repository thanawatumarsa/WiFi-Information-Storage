<template>
  <div id="app" class="container">
    <div class="page-header">
      <h1>Access Point Lists</h1>
    </div>
    <add-form :addAP = "addAP" :newInfo = "newInfo" :editInfo = "editInfo" :editChk = "editChk" :editWifi = "editWifi" :clearEdit = "clearEdit" :saveEdit = "saveEdit"
     :locationsChk = "locationsChk" :APlo = "APlo" :addLocations = "addLocations" :editLocations = "editLocations" :clearLo = "clearLo" :APloData="APloData"></add-form>
    <hr>
    <access-point-lists :wifiInfo = "wifiInfo" :editInfo = "editInfo" :edit = "editWifi" :remove = "removeAP" :editLocations = "editLocations"
     :locationsChk = "locationsChk" :APloData = "APloData" :LoTemp = "LoTemp" :removeLo="removeLo"></access-point-lists>
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
        serial: '',
        mac: '',
        ip: '',
        locations: ''
      },
      editInfo: {
        apname: '',
        serial: '',
        mac: '',
        ip: '',
        locations: ''
      },
      APlo: {
        location: '',
        dbm: ''
      },
      APloData: {},
      LoTemp: 0,
      editData: {},
      locationDex: 0,
      tempEdit: 0,
      editChk: true,
      locationsChk: false
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
      this.newInfo.serial = ''
      this.newInfo.mac = ''
      this.newInfo.ip = ''
    },
    editWifi: function (dex, wifi) {
      this.editChk = false
      this.locationsChk = false
      this.editInfo.apname = this.wifiInfo[dex].apname
      this.editInfo.serial = this.wifiInfo[dex].serial
      this.editInfo.mac = this.wifiInfo[dex].mac
      this.editInfo.ip = this.wifiInfo[dex].ip
      this.editInfo.locations = this.wifiInfo[dex].locations
      this.tempEdit = dex
      this.editData = wifi
    },
    saveEdit: function () {
      wifiInfoRef.child(this.editData['.key']).update(this.editInfo)
      this.clearEdit ()
    },
    addLocations: function () {
      wifiInfoRef.child(this.APloData['.key']).child('locations').push(this.APlo)
      this.APlo.location = ''
      this.APlo.dbm = ''
    },
    editLocations: function (dex, wifi) {
      this.editChk = false
      this.locationsChk = true
      this.APloData = wifi
      this.LoTemp = wifiInfoRef.child(this.APloData['.key'])
      console.log(this.LoTemp);
    },
    clearEdit: function () {
      this.editInfo.apname = ''
      this.editInfo.serial = ''
      this.editInfo.mac = ''
      this.editInfo.ip = ''
      this.editChk = true
      this.tempEdit = 0
    },
    clearLo: function () {
      this.APlo.location = ''
      this.APlo.dbm = ''
      this.locationsChk = false
      this.editChk = true
    },
    removeAP: function (wifi) {
      wifiInfoRef.child(wifi['.key']).remove()
    },
    removeLo: function (wifi, dex) {
      console.log(dex);
      wifiInfoRef.child(wifi['.key']).child('locations').child(dex).remove()
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

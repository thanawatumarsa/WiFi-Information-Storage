<template>
  <div id="app" class="container">
    <div class="page-header">
      <h2>Access Point Lists</h2>
    </div>
    <add-form :addAP = "addAP" :newInfo = "newInfo" :editInfo = "editInfo" :editChk = "editChk" :editWifi = "editWifi" :clearEdit = "clearEdit" :saveEdit = "saveEdit"
     :locationsChk = "locationsChk" :APlo = "APlo" :editLocations = "editLocations" :editlo = "editlo" :clearLo = "clearLo"></add-form>
    <hr>
    <access-point-lists :wifiInfo = "wifiInfo" :editInfo = "editInfo" :edit = "editWifi" :remove = "removeAP" :editLocations = "editLocations"></access-point-lists>
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
      },
      editInfo: {
        apname: '',
        serial: '',
        mac: '',
        ip: '',
      },
      APlo: {
        location: '',
        dbm: ''
      },
      APloData: {},
      APloData2: {},
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
      this.editInfo.apname = this.wifiInfo[dex].apname
      this.editInfo.serial = this.wifiInfo[dex].serial
      this.editInfo.mac = this.wifiInfo[dex].mac
      this.editInfo.ip = this.wifiInfo[dex].ip
      this.tempEdit = dex
      this.editData = wifi
    },
    editLocations: function (dex, wifi) {
      this.editChk = false
      this.locationsChk = true
      this.locationDex = dex
      this.APloData2 = wifi
      this.APloData = wifi
      this.APloData.push{locations: 'test'}
    },
    editlo: function () {
      console.log(this.APlo);
      wifiInfoRef.child(this.APloData2['.key']).push(this.APlo)
    },
    saveEdit: function () {
      wifiInfoRef.child(this.editData['.key']).update(this.editInfo)
      this.clearEdit ()
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

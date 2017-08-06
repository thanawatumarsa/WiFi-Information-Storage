<template lang="html">
  <table class="table table">
  <!-- <table v-if="!locationsChk" class="table table"> -->
    <thead>
      <tr>
        <th>
          <center>
          #
        </center>
        </th>
        <th>
          <center>
          AP Name
          </center>
        </th>
        <th>
          <center>
          S/N
          </center>
        </th>
        <th>
          <center>
          MAC Address
          </center>
        </th>
        <th>
          <center>
          IP Address
          </center>
        </th>
        <th>
          <center>
          Locations
          </center>
        </th>
        <th>
          <center>
          dBm
          </center>
        </th>
        <th>
        </th>
        <th>
          <center>
            Options
          </center>
        </th>
        <th>
          <center>
            Delete
          </center>
        </th>
      </tr>
    </thead>
    <each-access-point :wifiInfo="wifiInfo" :editInfo = "editInfo" :edit = "edit" :remove="remove" :editLocations = "editLocations"
     :APloData="APloData" :LoTemp = "LoTemp" :locationsChk="locationsChk" :removeLo="removeLo"></each-access-point>
  </table>
  <!-- <table v-else-if="locationsChk === true" class="table table">
    <thead>
      <tr>
        <th>
          <center>
          Location
        </center>
        </th>
        <th>
          <center>
          dBm
          </center>
        </th>
      </tr>
    </thead>
    <each-location :wifiInfo="wifiInfo" :APloData="APloData" :LoTemp = "LoTemp"></each-location>
  </table> -->
</template>

<script>

import EachAccessPoint from '../components/EachAccessPoint'
import EachLocation from '../components/EachLocation'

export default {
  props: ['wifiInfo', 'editInfo', 'edit', 'remove', 'editLocations', 'locationsChk', 'APloData', 'LoTemp', 'removeLo'],
  components: {
    EachAccessPoint,
    EachLocation
  }
}
</script>

<style lang="css">
</style>

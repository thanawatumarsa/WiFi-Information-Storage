<template lang="html">
  <table class="table table">
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
          SSID
          </center>
        </th>
        <th>
          <center>
          Location
          </center>
        </th>
        <th>
          <center>
          Model
          </center>
        </th>
        <th>
          <center>
          Edit
          </center>
        </th>
        <th>
          <center>
          Delete
          </center>
        </th>
      </tr>
    </thead>
    <each-access-point :wifiInfo="wifiInfo" :editInfo = "editInfo" :edit = "edit" :remove="remove"></each-access-point>
  </table>
</template>

<script>

import EachAccessPoint from '../components/EachAccessPoint'

export default {
  props: ['wifiInfo', 'editInfo', 'edit', 'remove'],
  components: {
    EachAccessPoint
  }
}
</script>

<style lang="css">
</style>

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
    <each-access-point :wifiInfo="wifiInfo" :editInfo = "editInfo" :edit = "edit" :remove="remove" :editLocations = "editLocations"></each-access-point>
  </table>
</template>

<script>

import EachAccessPoint from '../components/EachAccessPoint'

export default {
  props: ['wifiInfo', 'editInfo', 'edit', 'remove', 'editLocations'],
  components: {
    EachAccessPoint
  }
}
</script>

<style lang="css">
</style>

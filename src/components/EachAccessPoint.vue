<template lang="html">
  <tbody>
    <tr v-for="(wifi, index) in wifiInfo">
      <td>
        {{index + 1}}
      </td>
      <td>
        {{wifi.apname}}
      </td>
      <td>
        {{wifi.ssid}}
      </td>
      <td>
        {{wifi.location}}
      </td>
      <td>
        {{wifi.model}}
      </td>
      <td>
        <input type="submit" class="btn btn-primary" value="Edit" v-on:click="edit(index)">
      </td>
      <td>
        <input type="submit" class="btn btn-primary" value="Delete" v-on:click="remove(wifi)">
      </td>
    </tr>
  </tbody>
  </template>

<script>

import EditAccessPoint from '../components/EditAccessPoint'

export default {
  props: ['wifiInfo', 'editInfo', 'edit', 'remove', 'temp'],
  components: {
    EditAccessPoint
  }
}
</script>

<style lang="css">
</style>

<template lang="html">
  <tbody>
  <!-- <tbody  v-if="!locationsChk" > -->
    <tr v-for="(wifi, index) in wifiInfo">
      <td>
        {{index + 1}}
      </td>
      <td>
        {{wifi.apname}}
      </td>
      <td>
        {{wifi.serial}}
      </td>
      <td>
        {{wifi.mac}}
      </td>
      <td>
        {{wifi.ip}}
      </td>
      <td bgcolor="#e0ebeb">
        <div v-for="(lo, index) in wifi.locations" class="">
          <div align = "center">
            {{lo.location}}
          </div>
        </div>
      </td>
      <td bgcolor="#e0ebeb">
        <div v-for="(lo, index) in wifi.locations" class="">
          <div>
            {{lo.dbm}}
            <a @click="removeLo(wifi, index)" type="button" name="button">x</a>
          </div>
        </div>
      </td>
      <td>
      </td>
      <td>
        <input type="submit" class="btn btn-primary" value="Edit AP" v-on:click="edit(index, wifi)">
        <input type="submit" class="btn btn-primary" value="Add Location" v-on:click="editLocations(index, wifi)">
      </td>
      <td>
        <input type="submit" class="btn btn-primary" value="Delete AP" v-on:click="remove(wifi)">
      </td>
    </tr>
  </tbody>
  <!-- <tbody  v-else-if="locationsChk" >
    <tr v-for="(wifi, index) in wifiInfo">
      <div v-for="(lo, index) in wifi.locations" class="">
        <td>
          {{lo.location}}
        </td>
        <td>
          {{lo.dbm}}
        </td>
      </div>
    </tr>
  </tbody> -->
  </template>

<script>

export default {
  props: ['wifiInfo', 'editInfo', 'edit', 'remove' , 'editLocations', 'APloData', 'LoTemp', 'locationsChk', 'removeLo']
}
</script>

<style lang="css">
</style>

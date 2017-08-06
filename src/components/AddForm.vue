<template lang="html">
  <form id="form" class="form-inline" v-on:submit.prevent="addAP" v-if="editChk">
    <h3>Add Access point</h3>
    <div class="form-group">
      <input type="text" id="name" class="form-control" placeholder="AP Name" v-model="newInfo.apname">
    </div>
    <div class="form-group">
      <input type="text" id="phone" class="form-control" placeholder="Serial" v-model="newInfo.serial">
    </div>
    <div class="form-group">
      <input type="text" id="email" class="form-control" placeholder="MAC" v-model="newInfo.mac">
    </div>
    <div class="form-group">
      <input type="text" id="email" class="form-control" placeholder="IP" v-model="newInfo.ip">
    </div>
    <input :disabled="newInfo.apname == ''"type="submit" class="btn btn-default" value="+ Add">
  </form>
  <form id="form" class="form-inline" v-on:submit.prevent="editWifi" v-else-if="!editChk && !locationsChk">
    <h3>Edit Access point</h3>
    <div class="form-group">
      <input type="text" id="name" class="form-control" placeholder="AP Name" v-model="editInfo.apname">
    </div>
    <div class="form-group">
      <input type="text" id="phone" class="form-control" placeholder="Serial" v-model="editInfo.serial">
    </div>
    <div class="form-group">
      <input type="text" id="email" class="form-control" placeholder="MAC" v-model="editInfo.mac">
    </div>
    <div class="form-group">
      <input type="text" id="email" class="form-control" placeholder="IP" v-model="editInfo.ip">
    </div>
    <input  @click="saveEdit" :disabled="editInfo.apname == '' || editInfo.serial == '' || editInfo.mac == '' || editInfo.ip == ''"type="submit" class="btn btn-default" value="Save">
    <input @click="clearEdit" type="submit" class="btn btn-default" value="cancel">
  </form>
  <form id="form" class="form-inline" v-on:submit.prevent="addLocations" v-else-if="locationsChk">
    <h3>Add Location (AP Name : {{APloData.apname}})</h3>
    <div class="form-group">
      <input type="text" id="name" class="form-control" placeholder="Location" v-model="APlo.location">
    </div>
    <div class="form-group">
      <input type="text" id="phone" class="form-control" placeholder="dBm" v-model="APlo.dbm">
    </div>
    <input :disabled="APlo.location == '' || APlo.dbm == ''"type="submit" class="btn btn-default" value="Add">
    <input @click="clearLo" type="submit" class="btn btn-default" value="cancel">
  </form>
</template>

<script>
export default {
  props: ['addAP', 'newInfo', 'editInfo', 'editChk', 'editWifi', 'clearEdit', 'saveEdit', 'locationsChk', 'APlo', 'addLocations', 'editLocations', 'clearLo', 'APloData']
}
</script>

<style lang="css">
</style>

<template lang="html">
  <form id="form" class="form-inline" v-on:submit.prevent="addAP" v-if="editChk">
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
    <input :disabled="newInfo.apname == '' || newInfo.ssid == '' || newInfo.location == '' || newInfo.model == ''"type="submit" class="btn btn-default" value="+ Add">
  </form>
  <form id="form" class="form-inline" v-on:submit.prevent="editWifi" v-else>
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
</template>

<script>
export default {
  props: ['addAP', 'newInfo', 'editInfo', 'editChk', 'editWifi', 'clearEdit', 'saveEdit']
}
</script>

<style lang="css">
</style>

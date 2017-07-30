<template lang="html">
  <form id="form" class="form-inline" v-on:submit.prevent="addAP">
    <div class="form-group">
      <input type="text" id="name" class="form-control" placeholder="AP Name" v-model="newInfo.apname">
    </div>
    <div class="form-group">
      <input type="text" id="phone" class="form-control" placeholder="SSID" v-model="newInfo.ssid">
    </div>
    <div class="form-group">
      <input type="text" id="email" class="form-control" placeholder="Location" v-model="newInfo.location">
    </div>
    <div class="form-group">
      <input type="text" id="email" class="form-control" placeholder="Model" v-model="newInfo.model">
    </div>
    <input :disabled="newInfo.apname == '' || newInfo.ssid == '' || newInfo.location == '' || newInfo.model == ''"type="submit" class="btn btn-default" value="+ Add">
  </form>
</template>

<script>
export default {
  props: ['addAP', 'newInfo']
}
</script>

<style lang="css">
</style>

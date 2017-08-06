<template lang="html">
  <tbody>
      <tr v-for="(lo, index) in APloData.locations">
        <td>
          {{lo.location}}
        </td>
        <td>
          {{lo.dbm}}
        </td>
      </tr>
    </div>
  </tbody>
</template>

<script>
export default {
  props: ['wifiInfo', 'APloData', 'LoTemp']
}
</script>

<style lang="css">
</style>

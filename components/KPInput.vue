<template>
<div class="kp-form-input" v-bind:class="[type === 'password' ? 'kp-form-input-password' : 'kp-form-input-text']">
  <input :type="type ? type : 'text'" v-bind="$attrs"
      v-on:input="$emit('input', $event.target.value)">
  <!-- <label for="id">아이디</label> -->
</div>
</template>

<script>
import Vue from 'vue';


export default Vue.extend({
  name: "kp-input",
  props : ['type'],
  data(){
    return {
      value : ''
    }
  }
})
</script>

<style scoped lang="scss">
</style>

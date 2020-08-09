<template>
<!-- <div class="kp-form-input" v-bind:class="[type === 'password' ? 'kp-form-input-password' : 'kp-form-input-text']">
  <input :type="type ? type : 'text'" v-bind="$attrs"
      v-on:input="$emit('input', $event.target.value)">
</div> -->

<div class="kp-form-select-outer">
      <select v-bind="$attrs" v-on:change="$emit('input', $event.target.value)">
    <slot></slot>
    </select>
    </div>
</template>

<script>
import Vue from 'vue';


export default Vue.extend({
  name: "kp-select",
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

<template>
<button class="kp-btn" :type="type ? type : 'submit'" v-bind="$attrs"><slot></slot></button>
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

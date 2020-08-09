<template>
<div class="kp-btn-toggle">
    <button type="button" class="kp-btn-toggle-item" :class="{'selected' : value === item.value}" v-for="item of list" v-bind:key="item.value" @click="onClick(item)">
        {{item.label || item.value}}
    </button>
</div>
</template>

<script>
import Vue from 'vue';


export default Vue.extend({
  name: "kp-btn-toggle",
  props : ['list'],
  data(){
      return {
          value : ''
      }
  },
  methods: {
      onClick(item){
          this.value = item.value;
          console.log(item.value);
          this.$emit('input', item.value);

      }
  }
})
</script>

<style scoped lang="scss">

</style>

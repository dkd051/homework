<template>
<promotion-modal></promotion-modal>
</template>
<script lang="ts">
import Vue from 'vue'
import PromotionModal from '~/components/PromotionModal.vue';
export default Vue.extend({
  name : 'promo',
  components: {
    PromotionModal,
  },
  data(){
    return {
      showModal : false
    }
  }
})
</script>

<style scoped>
div{
  height: 100vh;
  background: #fff;
}
.btn-main2{
  width: 100%;
  padding-top: 19.0666666667%;
  background-image: url(~assets/images/new/main_btn2.png);
}
</style>

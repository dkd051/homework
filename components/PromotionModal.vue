<template>
  <div class="page-promotion-modal" :class="{mounted : isMounted}">
  <div class="inner">
    <div class="top-section">
      <div class="blind">
        <h2>
          이벤트 계좌로 1원 보내봐!
        </h2>
      </div>
      <button class="btn-close" @click="$parent.showModal=false"><img src="~assets/images/new/btn_close.png" width="28.5" height="29.5" alt="닫기"></button>
  </div>
  <div class="bottom-section">
    <div class="bottom-section-inner">
      <img src="~assets/images/new/event_desc.png" class="event-desc" alt="">
    <div class="ir">
      <p>송금할 1원이 없다면?</p>
      <button class="btn-coupon">
        <img src="~assets/images/new/coupon_btn.png" alt="1원 쿠폰">
      </button>
    </div>
    <div class="ir">
      <ul>
        <li>송금 후 즉시 당첨 확인 가능 &amp; 1원 환불 (카카오페이 플러스친구 메시지로 안내)</li>
        <li>매일 10회 참여가능 / 매주 경품 변경</li>
        <li>카톡 최신 버전에만 참여 가능</li>
      </ul>
      <button class="btn-update">
        <img src="~assets/images/new/update_btn.png" alt="카카오톡 업데이트">
      </button>
    </div>
    </div>
  </div>
  <div class="fix-bottom">
    <!-- <img src="~assets/images/new/bg_gold_bottom.jpg" alt=""> -->
      <button class="btn-main2 ir" @click="showModal = true">참여하기</button>
    </div>
  </div>
</div>
</template>

<script>
import Vue from 'vue';
export default Vue.extend({
  name: "PromotionModal",
  scrollToTop: true,
  mounted() {
    document.querySelector('body').classList.add('open-modal');
    window.scrollTo(0,0);
  },
  created () {
    this.isMounted = true;

  },
  beforeDestroy(){
    document.querySelector('body').classList.remove('open-modal');
  },
  data(){
    return {
      isMounted : false
    }
  }
})
</script>

<style scoped lang="scss">
.page-promotion-modal {
	left: 0;
	top: 0;
	z-index: 200;
	width: 100%;
	position: relative;
	padding-top: 150%;

	.inner {
		position: absolute;
		width: 100%;
		min-height: 100vh;
		left: 0;
		top: 0;
		height: 100%;
		background: #000;
	}
}
.top-section {
	height: 50%;
	background-image: url(~assets/images/new/bg_gold_top.jpg);
	background-position: center bottom;
}
.bottom-section {
	height: 50%;
	background-image: url(~assets/images/new/bg_gold_bottom.jpg);
	background-position: center top;
	text-align: center;
}
.btn-main2 {
	width: 100%;
	padding-top: 19.0666666667%;
	background-image: url(/_nuxt/assets/images/new/main_btn2.png);
}
.fix-bottom {
	position: fixed;
	left: 0;
	bottom: 0;
	padding-bottom: calc(env(safe-area-inset-bottom));
	width: 100%;
	z-index: 10;
	transform: translateY(0);
	transition-delay: 2s;
}
.btn-close {
	position: fixed;
	right: 7%;
	top: 34px;
}

.bottom-section {
	.bottom-section-inner {
		width: 78%;
		max-width: 585px;
		margin: 0 auto;
		position: relative;
	}
}
.btn-coupon {
	width: 19.4871794872%;
	position: absolute;
	top: 17.7%;
	right: 3%;
}
.btn-update {
	width: 27.4336283186%;
	position: absolute;
	right: 8%;
	bottom: 5.9%;
}

.top-section {
	animation-name: section-top;
	animation-duration: 1.2s;
	animation-timing-function: ease-in;
	animation-direction: initial;
	animation-play-state: paused;
}
.bottom-section {
	animation-name: section-bottom;
	animation-duration: 1.2s;
	animation-timing-function: ease-in;
	animation-direction: initial;
}
.page-promotion-modal.mounted {
	.top-section {
		animation-play-state: running;
	}
	.bottom-section {
		animation-play-state: running;
	}
}

@keyframes section-top {
	0% {
		transform: translateY(-180%);
	}

	30% {
		transform: translateY(0);
	}

	35% {
		transform: translateY(-20%);
	}

	45% {
		transform: translateY(0);
	}

	50% {
		transform: translateY(0);
	}
}

@keyframes section-bottom {
	0% {
		transform: translateY(180%);
	}

	30% {
		transform: translateY(0);
	}

	35% {
		transform: translateY(20%);
	}

	45% {
		transform: translateY(0);
	}

	50% {
		transform: translateY(0);
	}
}

</style>

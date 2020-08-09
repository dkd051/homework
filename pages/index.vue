<template>
<div class="outer">
<promotion-modal v-if="showModal"></promotion-modal>
<div class="page-promotion-outer" :class="{'on-load' : onLoaded}" v-show="!showModal">
    <div class="top-bar">
        <p class="bi-remit ir">
          카카오페이 송금
        </p>
        <h5 class="top-bar-title ir">10주간의 현금스웩</h5>
        <p class="bi-smtm6 ir">
          쇼미더머니6
        </p>
      </div>
    <div class="content">
      <div class="section section-dropthemoney">
        <span class="spark1">
          <img src="~assets/images/new/spark1.png" alt="">
        </span>
        <span class="spark2">
          <img src="~assets/images/new/spark2.png" alt="">
        </span>
        <span class="spark3">
          <img src="~assets/images/new/spark3.png" alt="">
        </span>
        <img src="~assets/images/new/neon_txt_dropthe.png" class="txt-dropthe" alt="">
        <img src="~assets/images/new/neon_txt_money.png" class="txt-money pos-abs" alt="">
        <img src="~assets/images/new/neon_txt_o.png" class="txt-o pos-abs" alt="">
        <img src="~assets/images/new/txt_remit.png" class="pos-abs" alt="">
        <div class="blind">
          <h1>
            DROP THE MONEY 송금만해도 현금이 쏟아진다!
          </h1>
        </div>
      </div>
      <div class="section section-gmoney">
        <img src="~assets/images/new/g_money.png" class="g-money" alt="">
        <img src="~assets/images/new/left_hand.png" class="left-hand pos-abs" alt="">
        <img src="~assets/images/new/100_million_won.png" class="txt-million pos-abs" alt="총 1억원">
        <img src="~assets/images/new/right_hand.png" class="right-hand pos-abs" alt="">
      </div>
      <div class="section section-reward-desc">
        <img src="~assets/images/new/reward_desc.png" alt="">
        <p class="blind">
          1주차 6.30 ~ 7.6 추첨을 통해 카카오머니를 드립니다.
          백만원 1명, 1만원 100명, 1천원 1천명, 백원 15만명
        </p>
      </div>
      <div class="section section-share">
        <div class="share-frame pos-abs"></div>
        <div class="blind">
          <p>친구들도 우리와 함께 갑시다.</p>
        </div>
        <ul class="share-btn-list">
          <li><a href="#" class="share-btn ir share-btn1">카카오톡 공유</a>
            </li>
          <li><a href="#" class="share-btn ir share-btn2">카카오 스토리 공유</a>
            </li>
          <li><a href="#" class="share-btn ir share-btn3">페이스북 공유</a>
            </li>
          <li><a href="#" class="share-btn ir share-btn4">트위터 공유</a></li>
        </ul>
      </div>
      <div class="bottom-coins">
        <img src="~assets/images/new/bottom_coins.png" alt="">
      </div>
      <div class="coins">
        <div class="coin1" :style="coinStyleObject(0.05)"><img src="~assets/images/new/coin_top.png" alt=""></div>
        <div class="coin2" :style="coinStyleObject(0.2)"><img src="~assets/images/new/coin_middle.png" alt=""></div>
        <div class="coin3" :style="coinStyleObject(0.38)"><img src="~assets/images/new/coin_bottom.png" alt=""></div>
      </div>
      
    </div>
    <div class="fix-bottom">
      <button class="btn-main ir" @click="showModal = true">참여하기</button>
    </div>
    <div class="drop-coins">
      <img src="~assets/images/new/drop_coins.png" class="drop-coins" alt="">
    </div>
  </div>
</div>
  
</template>

<script lang="ts">
import Vue from 'vue'
import PromotionModal from '~/components/PromotionModal.vue';
export default Vue.extend({
  components: {
    PromotionModal,
  },
  methods:{
    detectWindowScrollY(e:any) {
      if(process.client){
        this.scrollY = window.scrollY;
      }
      
    },
    onLoad(){
      const self = this;
      setTimeout(function() {
        self.onLoaded = true;
      }, 100)
    },
    coinStyleObject(ratio:number): Object {
      if(this.scrollY > 100){
        return {transform:`translateY(${(this.scrollY-103) * (ratio || 0.2) * -1}px)`}
      }else{
        return {
        };
      }
      
    } 
  },
  mounted() {
    window.addEventListener('load', this.onLoad);
    window.addEventListener('scroll', this.detectWindowScrollY)
  },
  destroyed() {
    window.removeEventListener('load', this.onLoad);
    window.removeEventListener('scroll', this.detectWindowScrollY)
  },
  data(){
    return {
      showModal : false,
      onLoaded : false,
      scrollY : 0 as number
    }
  },

  
})
</script>

<style lang="scss">
.page-promotion-outer {
	min-height: 100vh;
	background-image: url(~assets/images/new/bg_promotion.jpg);
	background-attachment: fixed;
	background-position: center 8.5333333333%;
	position: relative;
	overflow: hidden;
}

.top-bar {
	height: 35px;
	display: flex;
	justify-content: space-between;
	align-items: center;
	border-bottom: 1px solid #644c37;
	background-color: rgba(0, 0, 0, 0.1);
}
.top-bar-title {
	background-image: url("~assets/images/new/txt_topbar.png");
	width: 88px;
	height: 11px;
	left: 0;
	right: 0;
	margin: auto;
	position: absolute;
}
.bi-remit {
	background-image: url("~assets/images/new/bi_remit.png");
	width: 55px;
	height: 11px;
	margin-left: 16px;
}

.bi-smtm6 {
	width: 112px;
	height: 77.5px;
	background-image: url("~assets/images/new/bi_smtm6.png");
	position: absolute;
	right: 0;
	top: 0;
	max-width: 30%;
}

.fix-bottom {
	position: fixed;
	left: 0;
	bottom: 0;
	padding-bottom: calc(env(safe-area-inset-bottom));
	width: 100%;
	z-index: 10;
}

.btn-main {
	width: 100%;
	padding-top: 19.7333333333%;
	background-image: url(~assets/images/new/main_btn.png);
}

.content {
	text-align: center;
	padding-bottom: 19.733%;
	.section {
		position: relative;
		.pos-abs {
			position: absolute;
			top: 0;
			left: 0;
			right: 0;
			margin-left: auto;
			margin-right: auto;
		}
	}
	.section-dropthemoney {
		display: inline-flex;
		.spark1,
		.spark2,
		.spark3 {
			width: 36.9333333333%;
			position: absolute;
			left: 0;
			top: 0;
			padding-left: 28%;
			padding-top: 23%;
			transition: padding 0.3s ease;
		}
		.spark1 {
			transition-delay: 0.6s;
		}
		.spark2 {
			transition-delay: 0.62s;
		}
		.spark3 {
			transition-delay: 0.68s;
		}
	}

	.share-frame {
		padding-top: 32.93%;
		background-image: url(~assets/images/new/share_frame.png);
	}
	.share-btn-list {
		width: 75.3333333333%;
		display: inline-flex;
		padding-top: 17%;
		position: relative;
		z-index: 1;
		li {
			width: 25%;
			.share-btn {
				padding-top: 62.3%;
			}
			&:nth-child(1) .share-btn {
				background-image: url("~assets/images/new/share_btn_01.png");
			}
			&:nth-child(2) .share-btn {
				background-image: url("~assets/images/new/share_btn_02.png");
			}
			&:nth-child(3) .share-btn {
				background-image: url("~assets/images/new/share_btn_03.png");
			}
			&:nth-child(4) .share-btn {
				background-image: url("~assets/images/new/share_btn_04.png");
			}
		}
	}
	.bottom-coins {
		margin-top: 25px;
	}
	.coins {
		position: absolute;
		width: 100%;
		top: 24%;
		will-change: transform;
		transform: translateY(-100%);
		transition: transform linear 0.5s;
		.coin1,
		.coin2,
		.coin3 {
			transition: transform cubic-bezier(0.58, 0.1, 0.3, 1) 0.75s;
		}
		.coin1 {
			position: relative;
			z-index: 1;
		}
		.coin2 {
			margin-top: -11%;
		}
	}
}

.drop-coins {
	position: absolute;
	left: 0;
	top: 0;
	width: 150%;
	z-index: 5;
	transform: translateY(-100%);
	transition: transform linear 1.5s;
	will-change: transform;
}
.page-promotion-outer.on-load {
	.drop-coins {
		transform: translateY(500%);
	}
	.coins {
		transform: translateY(0);
	}
}

.g-money {
	animation-timing-function: cubic-bezier(0.6, 0.1, 0.3, 1);
	animation: bounce2 0.65s;
	animation-iteration-count: infinite;
}
.page-promotion-outer.on-load {
	.sprinkle-coins {
		transform: translateY(100%);
	}
	.spark1,
	.spark2,
	.spark3 {
		padding: 0;
	}
}
.txt-dropthe,
.txt-money {
	animation-name: shine;
	animation-timing-function: cubic-bezier(0.165, 0.84, 0.44, 1);
	animation-duration: 1s;
	animation-direction: alternate;
	animation-iteration-count: infinite;
	animation-delay: 1.68s;
}
.txt-money {
	animation-delay: 1s;
	animation-delay: 2.68s;
}
.txt-o {
	animation-name: blink;
	animation-duration: 1.3s;
	animation-direction: alternate;
	animation-iteration-count: infinite;
	animation-timing-function: ease-out;
	animation-delay: 3.68s;
}
.txt-million {
	animation: bounce 0.65s;
	animation-iteration-count: infinite;
	animation-timing-function: cubic-bezier(0.6, 0.1, 0.3, 1);
}

.left-hand {
	animation: left_hand 0.65s;
	animation-iteration-count: infinite;
	animation-timing-function: cubic-bezier(0.6, 0.1, 0.3, 1);
	transform-origin: left bottom;
}

.right-hand {
	animation: right_hand 0.65s;
	animation-iteration-count: infinite;
	animation-timing-function: cubic-bezier(0.6, 0.1, 0.3, 1);
	transform-origin: right bottom;
}
.share-frame {
	animation-name: blink2;
	animation-duration: 2s;
	animation-direction: alternate;
	animation-iteration-count: infinite;
	animation-timing-function: ease-out;
}

.million {
	animation: bounce 0.6s;
	animation-iteration-count: infinite;
	animation-timing-function: cubic-bezier(0.6, 0.1, 0.3, 1);
}

@keyframes slideOutDown2 {
	0% {
		transform: translateY(-100%);
	}
	100% {
		transform: translateY(0%);
		display: none;
	}
}
@keyframes shine {
	0% {
		opacity: 1;
	}

	50% {
		opacity: 0.85;
	}
	100% {
		opacity: 1;
	}
}
@keyframes blink {
	50% {
		opacity: 0;
	}
}
@keyframes blink2 {
	10% {
		opacity: 0.6;
	}
	15% {
		opacity: 1;
	}
}

@keyframes bounce {
	0% {
		transform: scale(1);
	}

	100% {
		transform: scale(1.06);
	}
}
@keyframes bounce2 {
	0% {
		transform: translateY(1%);
	}

	100% {
		transform: translateY(0%);
	}
}

.left-hand {
	animation: hand_rotate_left 0.65s;
	animation-iteration-count: infinite;
	animation-timing-function: cubic-bezier(0.6, 0.1, 0.3, 1);
	transform-origin: left bottom;
}
.right-hand {
	animation: hand_rotate_right 0.65s;
	animation-iteration-count: infinite;
	animation-timing-function: cubic-bezier(0.6, 0.1, 0.3, 1);
	transform-origin: right bottom;
}
@keyframes hand_rotate_left {
	0% {
		transform: rotate(0);
	}
	25% {
		transform: rotate(-18deg);
	}

	100% {
		transform: rotate(0);
	}
}

@keyframes hand_rotate_right {
	0% {
		transform: none;
	}
	25% {
		transform: rotate(18deg);
	}

	100% {
		transform: rotate(0);
	}
}

@media (min-width: 750px) {
	.section-share,
	.fix-bottom {
		max-width: 750px;
		margin-left: auto;
		margin-right: auto;
		left: 0;
		right: 0;
	}
}


</style>

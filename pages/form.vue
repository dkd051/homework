<template>

<div class="container">
<form v-on:submit.prevent="onSubmit">
  <h1 class="kp-form-title">회원가입</h1>
<div class="kp-form-row">
  <kp-input placeholder="아이디" v-model="form.id"></kp-input>
</div>
<div class="kp-form-row">
  <kp-input type="password" placeholder="비밀번호" v-model="form.password"></kp-input>
</div>
<div class="kp-form-row">
  <kp-btn-toggle :list="[{label : '남자', value : 'male'}, {label : '여자', value : 'female'}]" v-model="form.gender">
  </kp-btn-toggle>
</div>
<div class="kp-form-row">
  <p class="kp-form-label">
    생일
  </p>
  <div class="kp-form-group">
    <kp-select v-model="form.bornYear">
      <option value="">년</option>
      <option :value="i" v-for="i in years" v-bind:key="i">{{i}}년</option>
    </kp-select>

  <kp-select v-model="form.bornMonth">
      <option value="">월</option>
      <option :value="i" v-for="i in 12" v-bind:key="i">{{i}}월</option>
    </kp-select>
    <kp-select v-model="form.bornDay">
      <option value="">일</option>
      <option :value="i" v-for="i in 31" v-bind:key="i">{{i}}일</option>
    </kp-select>
  </div>
</div>
<div class="kp-form-row">
  <p class="kp-form-label">전화</p>
  <div class="kp-form-group">
    <kp-select v-model="form.tel1">
      <option value="010">010</option>
      <option value="017">017</option>
      <option value="018">018</option>
      <option value="019">019</option>
    </kp-select>
    <kp-input v-model="form.tel2"></kp-input>
    <kp-btn type="button">
      인증
    </kp-btn>
    
  </div>
</div>
<div class="kp-form-row term-row">
  <div class="kp-form-group justify-between">
  <p>
      모든 약관 내용에 동의합니다.
  </p>
  <div class="kp-form-toggle">
    <label class="toggle" for="checkTerm"><input type="checkbox" id="checkTerm" v-model="form.checkTerm">
      <span class="slider"></span>
      </label>
  </div>
  </div>
</div>
<div class="fix-bottom">
<kp-btn full>
  가입하기
</kp-btn>
</div>
</form>

</div>
</template>

<script lang="ts">
import Vue from 'vue'
import KPInput from '~/components/KPInput.vue';
import KPBtnToggle from '~/components/KPBtnToggle.vue';
import KPSelect from '~/components/KPSelect.vue';
import KPBtn from '~/components/KPBtn.vue';
export default Vue.extend({
  components: {
    KPInput,
    KPBtnToggle,
  },
  computed:{

  },
  methods:{
    range(start:number, end:number) {
    const ans = [];
    for (let i = end; i >= start; i--) {
        ans.push(i);
    }
    return ans;
    },
    onSubmit(){
      console.log(this.form);
    }
  },
  data(){
    return {
      text : '',
      showModal : false,
      form : {
        id : '',
        gender : '',
        password : '',
        bornYear : '',
        bornMonth : '',
        bornDay : '',
        tel1 : '010',
        tel2 : '',
        checkTerm : false
      },
      years : [] as number[],
      daysOfMonth : []
    }
  },
  watch:{
    bornYear: function (val) {

    },
    bornMonth: function (val) {

    },
  },
  mounted(){
    this.years = this.range(1930, new Date().getFullYear());
  }
  
})
</script>

<style lang="scss">
.container {
	background: #fff;
	min-height: 100vh;
	padding-left: 15px;
	padding-right: 15px;
	padding-top: 30px;
}

.kp-form-title {
	font-size: 21px;
	font-weight: 500;
	margin-bottom: 20px;
}
$primary-color: #fee506;
$border-color: #ddd;
$form-height: 38px;
$font-size: 16px;
.kp-btn {
	font-size: $font-size;
}
.kp-form-row {
	position: relative;
	display: flex;
	align-items: center;
	font-size: $font-size;
	flex-wrap: wrap;
	justify-content: flex-start;
	& + .kp-form-row {
		margin-top: 10px;
	}
	.kp-form-col {
		flex: auto;
		text-align: center;
	}
	input[type="text"],
	input[type="password"] {
		border: 0;
		flex: auto;
		height: 100%;
		padding-left: 10px;
	}

	.kp-btn-toggle {
		display: flex;
		flex: auto;

		.kp-btn {
			flex: inherit;
			text-align: center;
			background-color: transparent;
			color: #000;
			> label {
				flex: inherit;
				height: 32px;
				display: flex;
				justify-content: center;
				align-items: center;
			}
		}
	}
	.kp-form-input {
		position: relative;
		display: flex;
		flex: auto;
		align-items: center;
		border: 1px solid #ddd;
		height: $form-height;
		input[type="text"] + label,
		input[type="password"] + label {
			position: absolute;
			padding-left: 10px;
		}
	}
	.kp-form-select-outer {
		flex: auto;
		display: flex;
		border: 1px solid $border-color;
		padding: 2px 0 2px 10px;
		min-width: 58px;
	}
	select {
		flex: auto;
		display: flex;

		width: 100%;
		height: 29px;
		padding: 7px 8px 6px 7px\9;
		font-size: 15px;
		line-height: 18px;
		color: #000;
		border: none;
		border-radius: 0;
		*height: auto;
		*margin-top: 3px;
		-webkit-appearance: none;

		background: #fff url(~assets/images/new/select_angle.gif) 100% 50%
			no-repeat !important;
		-webkit-background-size: 20px 8px !important;
		background-size: 20px 8px !important;
	}
}
.kp-form-group {
	display: flex;
	flex: auto;
	flex-wrap: wrap;
	align-items: center;
	> * + * {
		margin-left: 6px;
	}
}
.kp-form-toggle {
	.toggle {
		position: relative;
		display: inline-block;
		width: 60px;
		height: 34px;
	}

	.toggle input {
		opacity: 0;
		width: 0;
		height: 0;
	}

	.slider {
		position: absolute;
		cursor: pointer;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		background-color: #6e6e6e;
		transition: 0.4s;
	}

	.slider:before {
		position: absolute;
		content: "";
		height: 26px;
		width: 26px;
		left: 4px;
		bottom: 4px;
		background-color: white;
		transition: 0.4s;
		border-radius: 50%;
	}

	input:checked + .slider {
		background-color: $primary-color;
	}

	input:focus + .slider {
		outline: none;
	}

	input:checked + .slider:before {
		transform: translateX(26px);
	}

	.slider {
		border-radius: 34px;
	}
}

.kp-form-label {
	margin-right: 14px;
	flex: none;
	padding-top: 8px;
	padding-bottom: 8px;
}
.kp-btn {
	display: flex;
	justify-content: center;
	align-items: center;
	background-color: $primary-color;
	color: #000;
	font-weight: 600;
	height: $form-height;
	padding-left: 8px;
	padding-right: 8px;
}
.kp-btn[full] {
	width: 100%;
}
.kp-btn-toggle {
	display: flex;

	.kp-btn-toggle-item {
		flex: auto;
		height: $form-height;
		border: 1px solid $border-color;
		&.selected {
			background-color: $primary-color;
			color: #000;
			border-color: $primary-color;
			position: relative;
			&::after {
				width: 1px;
				height: 100%;
				position: absolute;
				left: -1px;
				top: 0;
				background-color: $primary-color;
				display: block;
				content: "";
			}
		}
	}
	.kp-btn-toggle-item + .kp-btn-toggle-item {
		border-left-width: 0;
	}
}
.justify-between {
	justify-content: space-between;
}
.kp-form-row.term-row {
	margin-top: 20px;
}
.fix-bottom {
	position: fixed;
	left: 0;
	bottom: 0;
	padding-bottom: calc(env(safe-area-inset-bottom));
	width: 100%;
	z-index: 10;
}

</style>

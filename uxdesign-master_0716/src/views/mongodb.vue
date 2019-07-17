<template>
  <div style="width:500px; margin:20px">
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      
      <!-- 이메일-->
      <b-form-group id="input-group-1">
        <b-form-input
          id="input-1"
          v-model="form.uid"
          type="email"
          required
          placeholder="이메일 입"
        ></b-form-input>
      </b-form-group>

      <!-- 패스워드 -->
      <b-form-group id="input-group-2">
        <b-form-input
          id="input-2"
          v-model="form.params.password"
          type="password"
          required
          placeholder="비밀번호 입력"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="warning">Submit</b-button> &nbsp;
      <b-button type="reset" variant="">Reset</b-button>
    </b-form>

    <!-- 결과창 -->
    <b-card class="mt-3" header="결과">
      <pre class="m-0" style="text-align:left">{{ form }}</pre>
      </b-card>
  </div>
</template>

<script>
// import indata from './insertdata';
  export default {
    data() {
      return {
        form: {
          ticket: '',
          timestamp: 0.0,
          uid: '', // 사용자 입력
          cmd: 'createAccount', // 지정된 값
          params: {
            password:"" //사용자 입력
          },
        },
        show: true
      }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
      },
      onReset(evt) {
        evt.preventDefault()
        // 값 초기화
        this.form.ticket = ''
        this.form.timestamp = 0.0
        this.form.uid = ''
        this.form.cmd = 'createAccount'
        this.form.params.password = ''
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    }
  }
</script>

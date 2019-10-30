<template>
  <div class="card-content">
    <nav-bar></nav-bar>
    <b-field label="Username" expanded>
      <b-input v-model="form.username" maxlength="30" expanded></b-input>
    </b-field>
    <b-field label="Password" expanded>
      <b-input type="password" v-model="form.password" maxlength="16" password-reveal></b-input>
    </b-field>
    <b-field v-if="$v.form.$dirty && $v.form.$invalid">
      <b-message type="is-danger" has-icon v-if="!$v.form.username.required">กรุณาใส่ชื่อผู้ใช้</b-message>
      <b-message
        type="is-danger"
        has-icon
        v-if="!$v.form.username.email"
      >ชื่อผู้ใช้ต้องเป็น Email ตัวอย่างเช่น xxx@xxx.com</b-message>
      <b-message type="is-danger" has-icon v-if="!$v.form.password.required">กรุณาใส่รหัสผ่าน</b-message>
      <b-message
        type="is-danger"
        has-icon
        v-if="!$v.form.password.minLength"
      >รหัสผ่านต้องมากกว่า 4 ตัวอักษร</b-message>
    </b-field>
    <b-field class="buttons" grouped>
      <b-button type="is-primary" @click="touch">Login</b-button>
      <b-button type="is-primary" @click="reset">Reset</b-button>
    </b-field>
    <p>Dirty : {{ $v.form.$dirty }}</p>
    <p>Invalid : {{ $v.form.$invalid }}</p>
    <p>Require username: {{ $v.form.username.required }}</p>
    <p>User name minLength 8-30: {{ $v.form.username.minLength }}</p>
    <p>Require password: {{ $v.form.password.required }}</p>
    <p>Password minLength 4-16: {{ $v.form.password.minLength }}</p>
  </div>
</template>
<script>
import NavBar from "./NavBar.vue";

import { required, minLength, email } from "vuelidate/lib/validators";

export default {
  components: {
    NavBar
  },
  data() {
    return {
      form: {
        username: "",
        password: ""
      }
    };
  },
  validations: {
    form: {
      username: {
        required,
        email
      },
      password: {
        required,
        minLength: minLength(4)
      }
    }
  },
  methods: {
    touch() {
      this.$v.form.$touch();
    },
    reset() {
      this.$v.form.$reset();
    }
  }
};
</script>
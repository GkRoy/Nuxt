<template>
  <b-container>
    <b-row align-h="center">
      <b-col cols="12" md="auto">
        <h3 class="text-center">Log-in</h3>
        <b-form @submit="userLogin">
          <b-form-group
            id="input-group-1"
            label="Email address:"
            label-for="input-1"
            description="We'll never share your email with anyone else."
          >
            <b-form-input
              id="input-1"
              v-model="login.username"
              type="email"
              required
              placeholder="Enter email"
            ></b-form-input>
          </b-form-group>

          <b-form-group
            id="input-group-2"
            label="Your Password:"
            label-for="input-2"
          >
            <b-form-input
              id="input-2"
              v-model="login.password"
              required
              placeholder="Enter password"
              type="password"
            ></b-form-input>
          </b-form-group>

          <div class="text-center">
            <b-button type="submit" variant="primary">Login</b-button>
          </div>
        </b-form>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import axios from "axios";

export default {

  data() {
    return {
      login: {
        username: '',
        password: ''
      }
    }
  },

  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('https://api-test.comunal.co/session', { data: this.login })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  },

  head() {
    return {
      title: 'Login page 🚀',
      meta: [
        { hid: 'Login', name: 'This is the login page', content: 'Login page page is for ...' }
      ],
      noscript: [
        { innerHTML: 'Body No Scripts', body: true }
      ]
    }
  },
};
</script>
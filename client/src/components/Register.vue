<template>
  <v-layout column>
    <v-flex xs6 offset-xs3 align-center>
      <div class="white elevation-2">
        <v-toolbar flat dense class="blue mt-5" >
          <v-toolbar-title>Register</v-toolbar-title>
        </v-toolbar>
        <div class="pl-4 pr-4 pt-2 pb-2">
          <div class="error" v-html="error"></div>
          <v-form v-model="valid">
            <v-text-field
              label="Email"
              v-model="email"
              required
            ></v-text-field>
            <v-text-field
              label="Password"
              v-model="password"
              type="password"
              required
            ></v-text-field>
          </v-form>
          <v-btn
            class="red"
            @click="register">
            Register
          </v-btn>
        </div>
      </div>
    </v-flex>
  </v-layout>

</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'

export default {
  name: 'Register',
  data () {
    return {
      valid: false,
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }

    }
  }
}
</script>

<style scoped>
  .error {
    color: red;
  }
</style>

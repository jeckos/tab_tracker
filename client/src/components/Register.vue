<template>
  <div>
    <input
      type="email"
      name="email"
      placeholder="Email"
      v-model="email"
    >
    <br>
    <input
      type="password"
      name="password"
      placeholder="Password"
      v-model="password"
    >
    <br>
    <button @click="register">Register</button>
  </div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'

export default {
  name: "Register",
  data () {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    async register () {
      const res = await AuthenticationService.register({
        email: this.email,
        password: this.password
      })
      console.log(res.data.message)
    }
  }
}
</script>

<style scoped>

</style>

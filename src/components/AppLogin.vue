<!-- src/components/Login.vue -->
<template>
  <div>
    <h2>Login</h2>
    <input v-model="email" type="email" placeholder="Email" />
    <input v-model="password" type="password" placeholder="Password" />
    <button @click="login">Login</button>
    <p v-if="error">{{ error }}</p>
  </div>
</template>

<script>
import { auth } from '../firebase/firebase'
import { signInWithEmailAndPassword } from 'firebase/auth'

export default {
  data() {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async login() {
      try {
        await signInWithEmailAndPassword(auth, this.email, this.password)
        console.log('Logged in successfully!')
      } catch (err) {
        this.error = err.message
        console.error('Error logging in:', err)
      }
    }
  }
}
</script>

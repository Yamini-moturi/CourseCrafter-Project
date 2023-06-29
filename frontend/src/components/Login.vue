<script>
import AuthService from '@/services/AuthService'

export default {
  data: () => ({
    username: '',
    password: '',
    loading: false,
    isRememberMe: false
  }),
  mounted() {
    if (AuthService.isLoggedIn()) {
      this.$router.push(`/`)
    }
  },
  methods: {
    async submit(event) {
      this.loading = true
      const res = await AuthService.login(
        { username: this.username, password: this.password },
        this.isRememberMe
      )
      if (!res.success) {
        alert(res.error)
        this.loading = false
      } else {
        this.$router.push(`/`)
      }
    }
  }
}
</script>

<template>
  <div class="flex-card">
    <v-card class="mx-auto" title="Login" max-width="700">
      <v-card-text>
        <v-form fast-fail @submit.prevent="submit">
          <v-text-field v-model="username" label="Enter username or email"></v-text-field>

          <v-text-field v-model="password" label="Password" type="password"></v-text-field>

          <v-checkbox v-model="isRememberMe" label="Remember Me?"></v-checkbox>

          <v-btn
            color="indigo"
            :loading="loading"
            type="submit"
            block
            class="mt-2"
            text="Signin"
          ></v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </div>
</template>


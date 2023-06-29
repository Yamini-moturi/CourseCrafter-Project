<script>
import imageLogo from '@/assets/images/umich-logo.jpg'
export default {
  data() {
    return {
      imageLogo: imageLogo
    }
  },
  methods: {
    navigate(routePath) {
      this.$router.push(`/${routePath}`)
    }
  }
}
</script>

<template>
  <v-app-bar color="#00274c">
    <v-img width="30" height="70" max-width="100" :src="imageLogo"></v-img>
    <v-btn variant="text" color="white" @click="navigate('')"> Web Programming</v-btn>
    <v-btn variant="text" color="white" @click="navigate('login')"> Login </v-btn>
    <v-btn variant="text" color="white" @click="navigate('register')"> Register </v-btn>
  </v-app-bar>
</template>

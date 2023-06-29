<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

import AuthService from '@/services/AuthService'
const user = ref(AuthService.getUser())

const router = useRouter()
const navigate = (routePath) => {
  router.push(`/${routePath}`)
}
const logout = () => {
  AuthService.logout()
  router.push(`/login`)
}
</script>

<template>
  <v-navigation-drawer expand-on-hover rail location="left">
    <v-list>
      <v-list-item
        :title="user.firstname"
        :subtitle="user.email"
        @click="navigate('profile')"
      >
    </v-list-item>
    </v-list>

    <v-divider></v-divider>

    <v-list density="compact" nav>
      <v-list-item
        prepend-icon="mdi-home"
        title="Home"
        @click="navigate('')"
        value="home"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-account"
        title="My Account"
        @click="navigate('account')"
        value="account"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-folder-multiple-image"
        title="My Images"
        @click="navigate('myImages')"
        value="myImages"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-image-plus-outline"
        title="Add Image"
        @click="navigate('addImage')"
        value="addImage"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-cloud-upload"
        title="Upload Files"
        @click="navigate('uploadFiles')"
        value="uploadFiles"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-image"
        title="Image Gallery"
        @click="navigate('imageGallery')"
        value="imageGallery"
      ></v-list-item>
      <v-list-item
        prepend-icon="mdi-account-group-outline"
        title="Users"
        value="users"
      ></v-list-item>
    </v-list>

    <template v-slot:append>
      <v-list density="compact" nav>
        <v-list-item prepend-icon="mdi-logout" title="Logout" @click="logout()"></v-list-item>
      </v-list>
    </template>
  </v-navigation-drawer>
</template>

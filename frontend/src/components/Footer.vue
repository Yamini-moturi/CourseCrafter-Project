<script>
export default {
  data: () => ({
    links: [
      {
        name: 'Home',
        path: '/'
      },
      {
        name: 'Profile',
        path: '/profile'
      },
      {
        name: 'Image Gallery',
        path: '/imageGallery'
      },
      {
        name: 'Upload Files',
        path: '/uploadFiles'
      },
      {
        name: 'MyImages',
        path: '/myImages'
      },
      {
        name: 'Add Image',
        path: '/addImage'
      }
    ]
  }),
  methods: {
    navigate(routePath) {
      this.$router.push(`${routePath}`)
    }
  }
}
</script>

<template>
  <div>
    
    <v-footer app="true">
      <v-row justify="center" no-gutters>
       
        <v-btn
          v-for="link in links"
          :key="link"
          variant="text"
          class="mx-2 text-none"
          rounded="xl"
          @click="navigate(link.path)"
        >
          {{ link.name }}
        </v-btn>
        <v-divider></v-divider> 
        <v-col class="text-center mt-4" cols="12">
          {{ new Date().getFullYear() }} — <strong>Esiea- Web Technology</strong>
        </v-col>
      </v-row>
    </v-footer>
  </div>
</template>

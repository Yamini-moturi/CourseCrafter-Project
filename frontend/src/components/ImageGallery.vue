<script>
export default {
  data() {
    return {
      isGrayScale: false,
      limit: 10
    }
  },
  methods: {
    async copyUrl(imageUrl) {
      await navigator.clipboard.writeText(imageUrl)
    },
    addImage() {
      this.$router.push(`/addImage`)
    }
  }
}
</script>

<template>
  <v-banner lines="two" icon="mdi-image" color="indigo-darken-4" class="my-4">
    <v-banner-text>
      "Welcome to our Image Gallery! Here, you can browse and interact with a diverse collection of
      images uploaded by our community members. From breath-taking landscapes to fascinating
      abstract art - there's something for everyone."
    </v-banner-text>

    <template v-slot:actions>
      <v-btn @click="addImage">Go to Add Image</v-btn>
    </template>
  </v-banner>
  <v-row>
    <v-col cols="10">
      <v-text-field v-model="limit" label="Number of Images"></v-text-field>
    </v-col>
    <v-col cols="2">
      <v-switch
        v-model="isGrayScale"
        label="Gray Scale"
        color="indigo-darken-3"
        :model-value="isGrayScale"
        hide-details
      ></v-switch>
    </v-col>
  </v-row>
  <v-card class="mx-5 my-2 pa-3">
    <v-row>
      <v-col
        v-for="n in parseInt(limit)"
        :key="n"
        class="d-flex child-flex"
        cols="3"
        sm="4"
        md="3"
        lg="2"
      >
        <v-card>
          <v-img
            :src="`https://picsum.photos/500/300?image=${n * 5 + 10}${
              isGrayScale ? '&grayscale' : ''
            }`"
            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${
              isGrayScale ? '&grayscale' : ''
            }`"
            aspect-ratio="1"
            cover
            class="bg-grey-lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular indeterminate color="grey-lighten-5"></v-progress-circular>
              </v-row>
            </template>
          </v-img>
          <p class="text-right pa-3">
            Copy Url .<v-icon
              icon="mdi-content-copy"
              @click="
                copyUrl(
                  `https://picsum.photos/500/300?image=${n * 5 + 10}${
                    isGrayScale ? '&grayscale' : ''
                  }`
                )
              "
            ></v-icon>
          </p>
        </v-card>
      </v-col>
    </v-row>
  </v-card>
</template>

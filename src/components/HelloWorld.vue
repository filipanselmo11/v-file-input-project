<template>
  <v-container>
    <div v-if="!isImageAttached">
      <v-file-input
        @change="imageAttached"
        label="File Input"
        dense
        v-model="image"
        outlined
      ></v-file-input>
    </div>
    <div v-else>
      <v-btn text>Olá eu sou um botão</v-btn>
    </div>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",
  data: () => ({
    image: null,
    isImageAttached: false,
  }),
  methods: {
    imageAttached() {
      this.isImageAttached = true;
      console.log('Click no botão pra ver a imagem.');
    },
  },
};
</script>

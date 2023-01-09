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
      <v-dialog
        v-model="imageDialog"
        width="500">
          <template v-slot:activator="{ on, attrs }">
            <v-btn
              color="blue"
              v-on="on"
              v-bind="attrs">
              Visualizar Imagem
            </v-btn>
          </template>
          <v-img :src="url"/>
      </v-dialog>
      <!-- <v-btn text color="blue">Visualizar Imagem</v-btn> -->
    </div>
  </v-container>
</template>

<script>
export default {
  name: "HelloWorld",
  data: () => ({
    image: null,
    isImageAttached: false,
    imageDialog: false,
    url: null,
  }),
  methods: {
    imageAttached() {
      this.isImageAttached = true;
      this.url = URL.createObjectURL(this.image);
      console.log('Click no botão pra ver a imagem.');
    },
  },
};
</script>

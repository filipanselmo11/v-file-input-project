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
      <v-dialog v-model="imageDialog" width="500">
        <template v-slot:activator="{ on, attrs }">
          <v-btn v-on="on" v-bind="attrs">Open</v-btn>
        </template>
        <v-card>
          <v-toolbar dense color="elevation-0">
            <v-spacer></v-spacer>
            <v-btn icon color="black" @click="imageDialog = false">
              <v-icon>mdi-close</v-icon>
            </v-btn>
          </v-toolbar>
          <v-row no-gutters>
            <v-img :src="url" contain></v-img>
          </v-row>
        </v-card>
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
      console.log(this.url);
      // console.log('Click no botão pra ver a imagem.');
    },
  },
};
</script>

<template>
  <v-container>
    <v-row>
      <v-col>
        <h2>Gallery Page</h2>
      </v-col>
    </v-row>
    <v-row>
      <v-col v-for="n in fruit" :key="n" cols="12" sm="6" lg="3">
        <v-dialog v-model="dialog[n]" width="500">
          <template v-slot:activator="{ on, attrs }">
            <v-hover v-slot="{ hover }">
              <v-card
                :elevation="hover ? 12 : 2"
                :class="{ 'on-hover': hover }"
                v-bind="attrs"
                v-on="on"
                @click="onOpen(n)"
              >
                <v-img
                  height="500"
                  :id="`image${n}`"
                  :src="require(`../assets/images/f_${n}.jpg`)"
                ></v-img>
              </v-card>
            </v-hover>
          </template>
          <v-hover v-slot="{ hover }">
            <v-card
              :elevation="hover ? 2 : 2"
              :class="{ 'on-hover': hover ? true : true }"
              class="pa-2"
            >
              <v-carousel hide-delimiters show-arrows-on-hover>
                <v-carousel-item
                  contain
                  :src="require(`../assets/images/f_${n}.jpg`)"
                ></v-carousel-item>
              </v-carousel>
            </v-card>
          </v-hover>
        </v-dialog>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      dialog: {},
      fruit: [
        "apple",
        "cherry",
        "orange",
        "peach",
        "resberry",
        "strawberry",
        "banana",
        "coconut",
        "grape",
        "kiwi",
        "mango",
        "pineapple",
      ],
      width: null,
    };
  },
  methods: {
    onOpen(n) {
      var img = document.getElementById(`image${n}`);
      console.log(img);
      //   var width = img.clientWidth;
      //   var height = img.clientHeight;
      //   console.log(width, height);
      //   this.width = width;
    },
  },
};
</script>

<style scoped>
.v-card {
  transition: opacity 0.4s ease-in-out;
}

.v-card:not(.on-hover) {
  opacity: 0.6;
}
</style>

<template>
  <v-app id="inspire">
    <v-app-bar app color="white" flat>
      <v-container class="py-0 fill-height">
        <v-avatar class="mr-10" color="grey darken-1" size="48">
          <v-img
            lazy-src="../assets/emb.png"
            max-height="35"
            max-width="35"
            src="../assets/emb.png"
          ></v-img>
        </v-avatar>

        <v-btn v-for="org in titles" :key="org" text>
          {{ org.name }}
        </v-btn>

        <v-spacer></v-spacer>

        <v-responsive max-width="260">
          <v-text-field
            dense
            flat
            hide-details
            rounded
            solo-inverted
          ></v-text-field>
        </v-responsive>
      </v-container>
    </v-app-bar>

    <v-main class="grey lighten-3">
      <v-container>
        <v-row>
          <v-col cols="2">
            <v-sheet rounded="lg">
              <v-list color="transparent">
                <v-list-item
                  v-for="n in links"
                  :key="n"
                  v-on:click="greet(n)"
                  link
                >
                  <v-list-item-content>
                    <v-list-item-title>  {{ n }} </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>

                <v-divider class="my-2"></v-divider>

                <v-list-item link color="grey lighten-4">
                  <v-list-item-content>
                    <v-list-item-title v-on:click="greet(1)"> Refresh </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-sheet>
          </v-col>

          <v-col>
            <v-sheet min-height="70vh" rounded="lg">
              <v-img id="cimage"
                lazy-src="../assets/9.png"
                max-height="900"
                max-width="900"
                :src="imageSource"
              ></v-img>
            </v-sheet>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "Fihuristh",
  // props: ["content"],
  methods: {
    greet: function (name) {
      this.imageSource =  require('../assets/'+name+'.png');
    },
  },
  data: () => ({
    links: ["1", "2", "3", "4.17", "9"],
    titles: [
      {
        name:"Mira",
        url: 'mira.gov.mv'
      }, 
      {
        name: "Majlis",
        url: "majlis.gov.mv"
      }],
    imageSource: require('../assets/1.png'),
  }),
};
</script>
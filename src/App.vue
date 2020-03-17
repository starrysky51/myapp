<template>
  <v-app>
    <v-content>
      <v-container>

        <v-card>
          <v-toolbar-title>items</v-toolbar-title>
          <button @click="getItems">getItems</button>
          {{ items }}
        </v-card>

      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import axios from 'axios'

export default {
  name: 'App',

  data () {
    return {
      items: null
    }
  },

  mounted: function() {
    this.getItems()
  },

  methods: {
    getItems: function () {
      const url = 'http://localhost:3000/items'
      axios.get(url)
        .then(res => {
          this.items = res.data
        })
    }
  }
};
</script>



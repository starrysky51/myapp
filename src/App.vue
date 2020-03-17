<template>
  <div>
  <button @click="getItems">getItems</button>
  <div>
    {{ items }}
  </div>
  </div>
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



<template>
  <div>
  <!-- <button @click="getItems">getItems</button> -->
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
    const items = axios.get('http://localhost:3000/items').then(res => { this.items = res.data})
    return {
      items,
      page:1,

    }
  },

  // computed: {
  //   filterItem(){
  //     return this.items.slice(0,3)
  //   } 
  // }

  // mounted: function() {
  //   this.getItems()
  // },

  // methods: {
  //   getItems: function () {
  //     const url = 'http://localhost:3000/items'
  //     axios.get(url)
  //       .then(res => {
  //         this.items = res.data.slice(0,)
  //       })
  //   }
  // }
};
</script>



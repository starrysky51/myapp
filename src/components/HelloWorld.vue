<template>
<div>{{ items }}</div>
</template>

<script>
import axios from 'axios'
import * as AxiosLogger from 'axios-logger'

const instance = axios.create()
instance.interceptors.response.use(AxiosLogger.responseLogger)

export default {
  name: 'Users',
  data () {
    return {
      page: 1,
      items: null,
      pagesize: 2
    }
  },
  mounted: function() {
    this.getItems()
  },
  methods: {
    getItems: function() {
      axios.get('http://localhost:3000/items')
      .then(res => {
        this.items = res.data.items
      })
      .catch(err => {
        console.error(err)
      })
    }
  }
}
</script>


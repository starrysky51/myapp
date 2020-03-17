<template>
  <v-app>
    <v-content>
      <v-container>
        <v-simple-table>
          <thead>
            <tr>
              <th>media_code</th>
              <th>name</th>
              <th>corps</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in paginatedItems"  :key="item.media_code">
              <th>{{ item.media_code }}</th>
              <th>{{ item.name }}</th>
              <th>{{ item.corps }}</th>
            </tr>
          </tbody>
        </v-simple-table>
        <v-pagination
          v-model="page"
          :length="pageLength"
          :visible="pageLimit"
          @input="jumpPagination"
          circle
          ></v-pagination>
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
      page: 1,
      pageLimit: 10,
      items: null,
      paginatedItems: null
    }
  },

  computed: {
    pageLength: function () {
      if (!this.items) {
        return 1
      }
      return Math.ceil(this.items.length / this.pageLimit)
    }
  },

  mounted: function() {
    this.init()
  },

  methods: {
    init: function () {
      axios.get('http://localhost:3000/items')
        .then(res => {
          this.items = res.data
          this.paginatedItems = res.data.slice(0, this.pageLimit)
        })
    },
    jumpPagination: function (page) {
      const start = (page - 1) * this.pageLimit
      const end = page * this.pageLimit
      this.paginatedItems = this.items.slice(start, end)
    }
  }
};
</script>



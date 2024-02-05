<template>
  <v-container class="">
    <v-responsive class="">
      <h2 class="align-center">Users List</h2>

      <v-btn aria-label="Refresh" @click="update" color="primary">
        <v-icon icon="mdi-refresh"></v-icon>
        <v-tooltip activator="parent" location="start">Refresh Table</v-tooltip>
      </v-btn>

      <v-data-table
        v-model:page="page"
        :headers="headers"
        :items="tabledata"
        :items-per-page="itemsPerPage"
      >
        <template v-slot:bottom>
          <div class="text-center pt-2">
            <v-pagination v-model="page" :length="pageCount"></v-pagination>
          </div>
        </template>
      </v-data-table>
    </v-responsive>
  </v-container>
</template>

<script>
import { onMounted} from 'vue'
import axios from "axios"

  export default {
    data () {
      return {
        page: 1,
        itemsPerPage: 5,
        headers: [
          { title: 'Name', key: 'name'},
          { title: 'Lastname', key: 'last_name' },
          { title: 'Email Address', key: 'email_address' },

        ],
        tabledata: [],
      }
    },
    computed: {
      pageCount () {
        return Math.ceil(this.tabledata.length / this.itemsPerPage)
      },
    },
methods: {
  update() {
    console.log('btn clicked')
    this.fetchItems()

  },

  fetchItems() {
    axios.get('/users')
  .then((response) => {

console.log(response.data);
this.tabledata = response.data;

})
  .catch(function (error) {
    // handle error
    alert(error);
  })
  },

},

mounted() {
       this.fetchItems()
    },

  }
</script>

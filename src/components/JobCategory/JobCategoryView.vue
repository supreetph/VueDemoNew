<template>
  <div>
 
  </div>

  <table border="1" class="table">
      <thead>
          <tr>
              <th>JobCategoryId</th>
              <th>JobCategory</th>
          </tr>
      </thead>
      <tbody>
          <tr v-for="items in jobCats" :key="items.jobCategoryId" >
              <td>
                  {{items.jobCategoryId}}
              </td>
              <td>
                  {{items.jobCategoryDescription}}
              </td>
          </tr>
      </tbody>
  </table>
</template>

<script>
import axios from 'axios'
export default {
    name:"JobCategoryView",
data () {
    return {
      jobCats: []
    }
},
async mounted () {
  await  axios
      .get('https://localhost:44306/api/JobCategory/')
      .then(response => (this.jobCats = response.data))
  }
}
</script>

<style>

</style>
<template>
<form @submit="Add" method="post">
  <label>JobCategoryID</label>
  
    <input type="text" v-model="jc.jobCategoryId" required />
 Job Category: <input type="text" v-model="jc.JobCategoryDescription" required />
  <br /><br />
  <button>add categories</button>
  </form>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
    
      jc:{
          jobCategoryId:0,
          JobCategoryDescription: ''
      },
      
      jobCats: [],
    };
  },
  methods: {
    Add(e) {
        console.log(this.jc.jobCategoryId,this.jc.JobCategoryDescription)
         axios
        .post("https://localhost:44306/api/JobCategory/",this.jc )
          
        e.preventDefault()
    //await axios
     //   .post("https://localhost:44306/api/JobCategory/",{
     //       body:this.jc
     //   } )
      //  .then((response) => (this.jobCats = response.data));
    },
  },
};
</script>

<style>
</style>
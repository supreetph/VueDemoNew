<template>
<form @submit="Add" method="post">
  <label>Body</label>
  
    <input type="text" v-model="jc.body" required />
 Title: <input type="text" v-model="jc.title" required />
  <br /><br />
  UserId:<input type="text" v-model="jc.userId" required />
  <button>Add Post</button>
  </form>
</template>

<script>
import axios from "axios";
import db from '../JobCategory/firbaseinit';
import fireDB from 'firebase'
export default {
  data() {
    return {
    
      jc:{
          title:'',
          body: '',
          userId:0
      },
      
      jobCats: [],
    };
  },
  methods: {
    Add(e) {
      e.preventDefault()
        console.log(this.jc.title,this.jc.body,this.jc.userId)
         //axios
        //.post("https://jsonplaceholder.typicode.com/posts",this.jc )
        fireDB.firestore().collection('posts').add(this.jc)
        //const dataBase=db.collection('posts').add(this.jc);
        //dataBase.add(this.jc)
        
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
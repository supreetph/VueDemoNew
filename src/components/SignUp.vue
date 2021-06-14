<template>
  <form >
      Email: <input type="email" v-model="email"><br>
      Password: <input type="password" v-model="password"><br>
      Role: <select v-model="role">
          <option value="developer">.Net Developer</option>
          <option value="tester">Tester</option>

      </select>
     <button @click="logvalues">signup</button>
  </form>

  <p>
      {{email}}
  </p>
  <p>
      {{password}}
  </p>
  <p>{{role}}</p>
</template>

<script>
//import axios from 'axios'
export default {
data(){
    return{
        email:'',
        password:'',
        role:''
    }
},
methods:{
    logvalues(){
        console.warn(this.email)
        
    }
}
}
</script>

<style>

</style>
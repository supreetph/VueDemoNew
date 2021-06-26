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
import db from './JobCategory/firbaseinit'
import firbaseuth from 'firebase'
export default {
data(){
    return{
        email:'',
        password:'',
        role:''
    }
},
methods:{
    logvalues(e){
        e.preventDefault()
        console.warn(this.email)
        firbaseuth.auth().createUserWithEmailAndPassword(this.email,this.password).then(data=>console.log(data))
        
    }
}
}
</script>

<style>

</style>
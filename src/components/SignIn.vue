<template>
  <h2>Log in</h2>
  <form action="">
    <div class="mb-3 row">
      <label for="Email" class="col-sm-2 col-form-label">Email</label>
      <div class="col-sm-3">
        <input
          type="text"
          class="form-control"
          id="Email"
          v-model="user.email"
        />
      </div>
    </div>
    <div class="mb-3 row">
      <label for="inputPassword" class="col-sm-2 col-form-label"
        >Password</label
      >
      <div class="col-sm-3">
        <input
          type="password"
          class="form-control"
          id="inputPassword"
          v-model="user.password"
        />
      </div>
    </div>
    <div class="mb-3 row">
      <button type="button" @click="Login" class="btn btn-primary col-sm-2">
        Sign In
      </button>
     <div class="alert alert-info" role="alert">
 {{this.Response}}
</div>
    </div>
  </form>
</template>

<script>
import db from './JobCategory/firbaseinit'
import firbaseuth from 'firebase'
export default {
  data() {
    return {
      user: {
        email: "",
        password: "",
      },
      Response:''
    };
  },
  methods: {
    Login(e) {
      e.preventDefault();
      console.log(this.user.email);
      firbaseuth.auth().signInWithEmailAndPassword(this.user.email,this.user.password).then(data=>console.log(JSON.stringify(data)))
      this.Response=data

    },
  },
};
</script>

<style>
</style>
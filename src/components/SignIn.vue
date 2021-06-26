<template>
<h2>Log in</h2>
  <form action="">
      <div class="mb-3 row">
    <label for="Email" class="col-sm-2 col-form-label">Email</label>
    <div class="col-sm-3">
      <input type="text"  class="form-control-plaintext" id="Email" value="email@example.com">
    </div>
  </div>
  <div class="mb-3 row">
    <label for="inputPassword" class="col-sm-2 col-form-label">Password</label>
    <div class="col-sm-3">
      <input type="password" class="form-control" id="inputPassword">
    </div>
  </div>
  <div class ="mb-3 row">
             

<button type="button" @click="Login" class="btn btn-primary col-sm-2">Sign In</button>
  </div>
  </form>
</template>

<script>
export default {

}
</script>

<style>

</style>
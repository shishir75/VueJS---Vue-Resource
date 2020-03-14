<template>
  <div class="container my-5">
    <div class="row">
      <div class="col--xs-12 col-sm-8 offset-sm-2 col-md-6 offset-md-3">
        <h1>Http</h1>
        <form action="">
          <div class="form-group">
            <label>Username</label>
            <input type="text" class="form-control" v-model="user.username">
          </div>
          <div class="form-group">
            <label>Email</label>
            <input type="text" class="form-control" v-model="user.email">
          </div>
          <button class="btn btn-info">Submit</button>
        </form>
      </div>
    </div>

  </div>
</template>

<script>


  export default {
    name: 'App',
    data() {
      return {
        user: {
          username: '',
          email: ''
        }
      };
    }

  }
</script>

<style>

</style>

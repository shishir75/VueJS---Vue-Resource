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
            <input type="email" class="form-control" v-model="user.email">
          </div>
          <button class="btn btn-info" @click.prevent="submit">Submit</button>
        </form>

        <hr>

        <button class="btn btn-primary" @click.prevent="fetchData">Get Data</button>
        <hr>
        <ul class="list-group">
          <li class="list-group-item" v-for="u in users" :key="u">{{ u.username }} - {{ u.email }}</li>
        </ul>

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
        },
        users: [],
      };
    },
    methods: {
      submit() {
        this.$http.post('https://vuejs-http-737e3.firebaseio.com/data.json', this.user)
                  .then(response => {
                    console.log(response);
                  }, error => {
                    console.log(error);
                  });
      },

      fetchData() {
        this.$http.get('https://vuejs-http-737e3.firebaseio.com/data.json')
              .then(response => {
                  return response.json();
              })
              .then(data => {
                  const resultArray = [];
                  for (let key in data) {
                    resultArray.push(data[key]);
                  }

                  this.users = resultArray;
              });
      }
    }

  }
</script>

<style>

</style>

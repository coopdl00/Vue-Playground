<template lang="html">
  <div>
    <h1>Users</h1>
    <div v-for="user in userList" class="container">
      <b-card>
        <b-media>
          <div class="row">
            <div class="col-4">
              <img :src="user.photo_url" alt="">
            </div>
            <div class="col-8">
              <ul>
                <li>Name: {{user.name}}</li>
                <li>Phone: {{user.phone}}</li>
                <li>Email: {{user.email}}</li>
                <li>Company: {{user.company}}</li>
                <li>Address: {{user.address}}</li>
                <li>password: {{user.password}}</li>
              </ul>
            </div>
          </div>
        </b-media>
      </b-card>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Users',
  props: {
    users: {
      type: Array
    }
  },
  data () {
    return {
      userList: this.users
    }
  }
}
</script>

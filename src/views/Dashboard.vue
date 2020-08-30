<template>
  <div class="dashboard">
    <h1>hello {{ username }}</h1>
    <router-link :to="path">Your Profile</router-link>
    <router-view></router-view>
  </div>
</template>

<script>

export default {
  name: 'Dashboard',
  computed: {
    username() {
      return this.$route.params.username
    },
    path() {
      return this.$route.path + '/profile'
    }
  }
}

</script>

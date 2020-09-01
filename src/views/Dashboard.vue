<template>
  <div class="dashboard">
    <h1>hello {{ username }}</h1>
    <router-link :to="path">Your Profile</router-link>
    <Todoist />
    <router-view></router-view>
  </div>
</template>

<script>
import Todoist from "@/components/Todoist";

export default {
  name: 'Dashboard',
  components: {Todoist},
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

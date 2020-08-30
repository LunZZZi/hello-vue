<template>
  <div class="home">
    <Todoist />
  </div>
</template>

<script>
// @ is an alias to /src
import Todoist from "@/components/Todoist";

export default {
  name: 'Home',
  components: {
    Todoist
  }
}

</script>

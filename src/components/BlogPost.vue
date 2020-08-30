<template>
  <div class="blog-post">
    <h3>{{ post.title }}</h3>
    <CustomInput v-model="searchText" />
    <button v-on:click="$emit('enlarge-text')">Enlarge text</button>
    <div>{{ searchText }}</div>
    <div v-html="post.content"></div>
  </div>
</template>

<script>
import CustomInput from './CustomInput';

export default {
  name: 'BlogPost',
  components: {
    CustomInput
  },
  props: {
    post: Object
  },
  data() {
    return {
      searchText: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

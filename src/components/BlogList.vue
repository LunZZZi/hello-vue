<template>
  <div class="blog-list">
    <div :style="{ fontSize: postFontSize + 'em' }">
      <BlogPost 
        v-for="post in posts"
        v-bind:key="post.id"
        v-bind:post="post"
        v-on:enlarge-text="postFontSize += 0.1"
      />
    </div>
  </div>
</template>

<script>
import BlogPost from './BlogPost';

export default {
  name: 'BlogList',
  components: {
    BlogPost
  },
  data() {
    return {
      posts: [
        { id: 1, title: 'My journey with Vue', content: 'fuck' },
        { id: 2, title: 'logging with Vue', content: 'abc111' },
      ],
      postFontSize: 1
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

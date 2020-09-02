<template>
  <a v-bind:href="url" class="nav-link">
    <slot>Submit</slot>
  </a>
</template>

<script>
export default {
  name: 'NavLink',
  props: ['href', 'url']
}
</script>

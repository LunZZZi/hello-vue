<template>
  <div class="home">
    <ElButton @click="visible = true">Button</ElButton>
    <ElDialog :visible.sync="visible" title="Hello World">
      <p>Try Element</p>
    </ElDialog>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  data() {
    return {
      visible: false
    }
  }
}

</script>

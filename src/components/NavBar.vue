<template>
  <div class="nav-bar">
    <button v-on:click="toggle" @mouseenter="enterMenu" @mouseleave="leaveMenu">菜单</button>
    <transition name="fade">
      <div v-if="show" class="sub-menu" @mouseenter="enterMenu" @mouseleave="leaveMenu">
        <div>111</div>
        <div>222</div>
        <div>333</div>
      </div>
    </transition>
  </div>
</template>

<script>

export default {
  name: 'NavBar',
  data: function () {
    return {
      show: false,
      timer: null
    }
  },
  methods: {
    toggle() {
      this.show = !this.show;
    },
    enterMenu: function() {
      clearTimeout(this.timer);
      this.show = true;
    },
    leaveMenu: function () {
      this.timer = setTimeout(() => { this.show = false }, 500);
    }
  }
}
</script>

<style scoped>
.nav-bar {
  position: relative;
}
.sub-menu {
  position: absolute;
  width: 400px;
  background-color: #fff;
  padding: 20px;
  border: 1px solid #eee;
  border-radius: 5px;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>

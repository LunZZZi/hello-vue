<template>
  <div class="list-counter">
    <button v-bind:class="{ active: this.filter === 'all' }"
            v-on:click="$emit('change-filter', 'all')">All: {{ stt.all }}</button>
    <button v-bind:class="{ active: this.filter === 'checked' }"
            v-on:click="$emit('change-filter', 'checked')">done: {{ stt.checked }}</button>
    <button v-bind:class="{ active: this.filter === 'unchecked' } "
            v-on:click="$emit('change-filter', 'unchecked')">todo: {{ stt.unchecked }}</button>
  </div>
</template>

<script>
export default {
  name: 'ListCounter',
  props: {
    data: Array,
    changeFilter: Function,
    filter: String
  },
  computed: {
    stt() {
      const checked = this.data.filter(x => x.checked).length;
      const unchecked = this.data.filter(x => !x.checked).length;
      return {
        all: checked + unchecked,
        checked,
        unchecked
      }
    }
  }
}
</script>

<style scoped>
.list-counter {
}
button {
  margin-right: 15px;
}
button.active::before {
  content: ' ';
  width: 0;
  height: 0;
  position: absolute;
  margin-left: -15px;
  margin-top: 7px;
  border: 5px solid transparent;
  border-left-color: red;
  transform: translateY(-50%);
}
</style>

<template>
  <div class="list-item">
    <label>
      <input
        type="checkbox"
        v-bind:checked="data.checked"
        v-on:input="$emit('check', $event, data)"
      />
      <span v-bind:class="{ checked: data.checked }">{{ data.text }}</span>
    </label>
    <span class="remove"
          v-on:click="$emit('remove', data.id)">x</span>
  </div>
</template>

<script>

export default {
  name: 'ListItem',
  props: {
    data: Object
  }
}
</script>

<style scoped>
  .list-item {
    padding: 5px 0;
    display: flex;
    align-items: center;
  }
  .list-item:nth-of-type(n + 2) {
    border-top: 1px solid #eee;
  }
  .list-item span {
    margin-left: 5px;
  }
  .list-item span.checked {
    color: red;
    text-decoration:line-through;
  }
  .remove {
    margin-left: 5px;
    font-size: 16px;
    cursor: pointer;
  }
  .remove:hover {
    font-weight: 700;
  }
</style>

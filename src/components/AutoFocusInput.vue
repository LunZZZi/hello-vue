<template>
  <input type="text" v-focus.foo.bar.lalal />
</template>

<script>
export default {
  name: 'AutoFocusInput',
  directives: {
    focus: {
      inserted: function(el) {
        el.focus()
      },
      bind: function (el, binding) {
        const modifiers = binding.modifiers;
        console.log(modifiers);
      }
    }
  }
}
</script>

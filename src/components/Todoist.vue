<template>
  <div class="hello">
    <h1>Vue Todoist</h1>
    <span>input todo:</span>
    <input v-model="text" v-on:keyup.enter="submit" />

    <div class="list-counter">
      <ListCounter v-bind:data="todos" v-bind:filter="filter" v-on:change-filter="changeFilter" />
    </div>

    <div class="list-wrapper">
      <ListItem
        v-for="item in displayList"
        v-bind:key="item.id"
        v-bind:data="item"
        v-on:remove="remove"
        v-on:check="check"
      />
    </div>
  </div>
</template>

<script>
// import ButtonCounter from './ButtonCounter';
// import BlogList from './BlogList';
import ListItem from './ListItem';
import ListCounter from './ListCounter';

export default {
  name: 'Todoist',
  props: {
    msg: String
  },
  components: {
    ListCounter,
    ListItem
  },
  data() {
    const oldValue = localStorage.getItem('todos') || '[]';
    const todos = JSON.parse(oldValue);
    return {
      text: '',
      filter: 'all',
      todos
    }
  },
  watch: {
    todos: function() {
      this.saveLocal()
    }
  },
  computed: {
    displayList() {
      if (this.filter === 'all') {
        return this.todos;
      } else {
        return this.todos.filter(x => this.filter === 'checked' ? x.checked : !x.checked)
      }
    }
  },
  methods: {
    submit() {
      this.todos.push({
        id: Date.now(),
        text: this.text,
        checked: false
      });
      this.text = '';
    },
    changeFilter(type) {
      this.filter = type;
    },
    remove(id) {
      this.todos = this.todos.filter(x => x.id !== id)
    },
    check(event, data) {
      const index = this.todos.findIndex(x => x.id === data.id);
      this.todos[index].checked = event.target.checked;
      this.saveLocal();
    },
    saveLocal() {
      localStorage.setItem(
        'todos',
        JSON.stringify(this.todos.map(x => ({ id: x.id, text: x.text, checked: x.checked })))
      )
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  border: 1px solid #eee;
  margin: 0 auto;
  padding: 10px 20px 20px;
}
.list-wrapper {
  margin-top: 10px;
}
.list-counter {
  margin-top: 10px;
}
</style>

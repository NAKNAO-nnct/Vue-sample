<template>
  <div id="app">
    <input v-model="name" />
    <button v-on:click="todoAdd">追加</button>

    <ul>
      <li v-for="item in list" v-bind:key="item.id">
        {{ item.id }} : {{ item.name }}
        <button v-on:click="todoRemove(index)">削除</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "todo",
      list: [],
      next_id: 1
    };
  },
  methods: {
    todoAdd: function() {
      this.list.push({
        id: this.next_id,
        name: this.name
      });
      this.next_id += 1;
    },
    todoRemove: function(index) {
      this.list.splice(index, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

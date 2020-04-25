<template>
  <div id="app">
    <p class="error">{{ message }}</p>
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
      name: "",
      list: [],
      next_id: 1,
      message: ""
    };
  },
  methods: {
    todoAdd: function() {
      // 値チェック
      if (this.name.replace(" ", "").replace("　", "") == "") {
        this.message = "無効な入力です";
        return;
      }

      // listに追加
      this.list.push({
        id: this.next_id,
        name: this.name
      });
      // IDの更新
      this.next_id += 1;

      // 追加ボックス内の文字の消去
      this.name = "";

      this.message = "";
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

.error {
  color: red;
}
</style>

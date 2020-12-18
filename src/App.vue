<template>
  <div id="app">
    <input v-model="message">
    <input :value="message" @input="handleChange">
    {{message}}
    <!-- <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />-->
    <todo-list>
      <todo-item
        @delete="handleDelete"
        v-for="item in list"
        :key="item.title"
        data-test="dd"
        :title="item.title"
        :del="item.del"
      >
        <template v-slot:pre-icon="{value}">
          <span>⏩ {{value}}</span>
        </template>
      </todo-item>
    </todo-list>
    <el-date-picker></el-date-picker>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "app",
  components: {
    TodoItem,
    TodoList
  },
  data() {
    return {
      message: "hello world",
      list: [
        {
          title: "课程1",
          del: false
        },
        {
          title: "课程2",
          del: true
        },
        {
          title: "课程3",
          del: false
        },
        {
          title: "课程4",
          del: true
        }
      ]
    };
  },
  methods: {
    handleDelete(val) {
      console.log("handleDelete", val);
    },
    handleChange(e) {
      this.message = e.target.value
    }
  }
};
</script>

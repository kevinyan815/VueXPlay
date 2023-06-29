<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>

    <input v-model="message">
    <input :value="message" @input="handleChange">
    {{message}} {{message + message}}
    <div :id="message"></div>
    <!-- <ul>
        <todo-item v-for="item in list" :title="item.title" :del="item.del"></todo-item>
    </ul> -->
    <todo-list>
        <todo-item @delete="handleDelete" v-for="(item, index) in list" :key="index" :title="item.title" :del="item.del">
            <template v-slot:pre-icon="{value}">
                <span>前置图标 {{value}}</span>
            </template>
        </todo-item>
    </todo-list>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TodoList from './components/TodoList.vue'
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'App',
  components: {// 要使用的非全局组件需要在这里注册
    HelloWorld,
    TodoList,
    TodoItem
  },
  data() {
    return {
      message: 'HelloWorld',
      list: [
        {
          title: '课程1',
          del: false
        }, {
          title: '课程2',
          del: true
        }
      ]
    }
  },
  methods: {
    handleChange(e) {
      this.message = e.target.value
    },
    handleDelete(val) {
      console.log('handleDelete', val)
    }
  }

}
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

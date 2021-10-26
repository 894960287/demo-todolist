<template>
  <div>
    <h1>App根组件</h1>

    <hr>
    <todo-input @add="onAddNewTask"></todo-input>
    <todo-list :list="todolist"></todo-list>
    <hr>
    <todo-button v-model:active="activeBtnIndex" :list="tasklist"></todo-button>
  </div>
</template>


<script>
  // 导入 TodoList 组件
  import TodoList from './components/todo-list/TodoList.vue'
  import TodoInput from './components/todo-input/TodoInput.vue'
  // import TodoButton from './components/todo-button/TodoButton'
  import TodoButton from './components/todo-button/TodoButton.vue'

  export default {
    name: 'MyApp',
    data() {
      return {
        todolist: [{
            id: 1,
            task: '周一早上9点开会',
            done: false
          },
          {
            id: 2,
            task: '周一晚上8点聚餐',
            done: false
          },
          {
            id: 3,
            task: '周三早上演讲稿',
            done: true
          },
        ],
        activeBtnIndex: 0,
        nextId: 4
      }
    },
    methods: {
      onAddNewTask(taskname) {
        this.todolist.push({
          id: this.nextId,
          task: taskname,
          done: false
        })
        this.nextId++
      }
    },
    components: {
      "todo-list": TodoList,
      "todo-input": TodoInput,
      "todo-button": TodoButton
    },
    computed: {
      // 根据激活按钮的索引值，动态计算要展示的列表数据
      tasklist() {
        //对 “源数据” 进行 switch ... case 的匹配， 并返回计算之后的结果
        switch (this.activeBtnIndex) {
          case 0:
            return this.todolist
          case 1:
            return this.todolist.filter(x => x.done === true)
          case 2:
            return this.todolist.filter(x => !x.done !== false)
        }
      }
    }

  }
</script>

<style lang="less" scoped>

</style>
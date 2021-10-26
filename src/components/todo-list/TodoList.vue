<template>
  <div>
    <ul class="list-group">
      <li v-for="item in list" :key="item.id">
        <div>
          <input type="checkbox" class="custom1" :id="item.id" v-model="item.done">
          <label class="custom1" :class="item.done ? 'delete' : '' " :for="customCheck"> {{ item.task }} </label>
          <span v-if="item.done">---------------------完成</span>
          <span v-else="item.done">---------------------未完成</span>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'TodoList',
    props: {
      list: {
        type: Array,
        required: true,
        default: []
      }
    }
  }
</script>

<style lang="less">
  .list-group {
    width: 400px;
    font-size: 18px;
  }

  .delete {
    text-decoration: line-through;
    color: gray;
    font-style: italic;
  }
</style>
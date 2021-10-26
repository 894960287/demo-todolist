<template>
  <div>
    <form @submit.prevent="onFormSubmit">
      <input type="text" placeholder="请输入添加任务" v-model.trim="taskname">
      <button type="submit">添加新任务</button>
    </form>
    <hr>

  </div>
</template>

<script>
  export default {
    name: "TodoInput",
    emits: ['add'],
    data() {
      return {
        tasknameL: ''
      }
    },
    methods: {
      onFormSubmit() {
        if (!this.taskname) return alert('任务不能为空')

        this.$emit('add', this.taskname)

        this.taskname = ''
      }
    },
  }
</script>

<style lang="less" scoped>

</style>
<template>
  <div>
    <div class="button-group">
      <button type="button" :class="active ===0 ? 'green' : '' " @click="onBtnClick(0)">全部完成</button>
      <button type="button" :class="active ===1 ? 'green' : '' " @click="onBtnClick(1)">完成</button>
      <button type=" button" :class="active ===2 ? 'green' : '' " @click="onBtnClick(2)">未完成</button>
    </div>
  </div>
</template>

<script>
  export default {
    name: "TodoButton",
    // 声明一个自定义 事件，指向一个数组
    emits: ['update:active'],
    props: {
      active: {
        type: Number,
        required: true,
        // 默认激活索引值为 0  （全部 0 ，， 未完成  2   ，， 完成  1）
        default: 0
      }
    },
    methods: {
      onBtnClick(index) {
        if (index === this.active) return

        this.$emit('update:active', index)
      }
    },
  }
</script>

<style lang="less">
  .red {
    background-color: red;
  }

  .green {
    background-color: green;
  }
</style>
<template>
  <header class="header">
    <h1>todos</h1>
    <input id="toggle-all" class="toggle-all" type="checkbox" v-model="isAll" />
    <label for="toggle-all"></label>
    <input
      class="new-todo"
      placeholder="输入任务名称-回车确认"
      autofocus
      @keydown.enter="downFn"
      v-model="task"
    />
  </header>
</template>

<script>
export default {
  props: ['arr'],
  data() {
    return {
      task: "",
    };
  },
  methods: {
    downFn() {
      this.$emit("create", this.task);
      this.task = "";
    },
  },
  computed: {
    isAll: {
      set(val) {
        // 7. 全选框 - 选中状态(true/false)
        this.arr.forEach((obj) => (obj.isDone = val));
      },
      get() {
        // 6. 统计小选框状态 ->  全选状态
        // every口诀: 查找数组里"不符合"条件, 直接原地返回false
        return this.arr.length !==0 &&this.arr.every((obj) => obj.isDone === true);
      },
    },
  },
};
</script>
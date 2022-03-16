<template>
  <ul class="todo-list">
    <!-- completed: 完成的类名 -->
    <li v-for="obj in arr" :key="obj.id" :class="{completed:obj.isDone}" >
      <div class="view" >
        <input class="toggle" type="checkbox" v-model="obj.isDone"/>
        <label>{{obj.name}}</label>
        <button @click="delFn(obj.id)" class="destroy"></button>
      </div>
    </li>
  </ul>
  
</template>

<script>
export default {
  props:['arr'],
  methods:{
    delFn(id){
      this.$emit('del',id)
    }
  }
}
</script>
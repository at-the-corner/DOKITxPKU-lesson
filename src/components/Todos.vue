<template>
  <div class="todos-container">
    <div class="add-btn" @click="addTodo">+</div>
    <div class="todos-box">
      <div v-if="todos.length" style="font-weight:bold">进行中</div>
      <div class="todo-item" v-for="(todo, index) in todos" :key="index">{{todo}}
        <span class="done-btn" @click="done(index)">done</span>
      </div>
    </div>
    <div class="dones-box">
      <div v-if="dones.length" style="font-weight:bold">已完成</div>
      <div class="done-item" v-for="(todo, index) in dones" :key="index">{{todo}}</div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Todos',
  data() {
    return {
      todos: [],
      dones: []
    }
  },
  methods: {
    addTodo() {
      let todo = prompt('请添加一条事项', '');
      if (todo) {
        this.todos.push(todo)
      }
    },
    done(index) {
      let done = this.todos.splice(index, 1)
      this.dones.unshift(done[0])
    }
  }
}
</script>

<style scoped>
.todos-container {
  width: 500px;
  min-height: 500px;
  margin: 0 auto;
  /* margin: 10px; */
  padding: 20px;
  /* border: 1px solid #002FA7; */
  border-radius: 5px;
  background-color: white;
  box-shadow: 0 8px 12px #ebedf0;
}
.add-btn{
  width: 40px;
  height: 40px;
  border-radius: 50px;
  background-color: #002fa7;
  color: #FFF;
  font-size: 30px;
  line-height: 40px;
  font-weight: bold;
  cursor: pointer;
}
.todo-item {
  width: 100%;
  height: 40px;
  font-size: 24px;
  line-height: 40px;
  margin-top: 10px;
  background-color: #002fa7;
  color: #FFF;
  position: relative;
}
.done-btn{
  display: none;
  position: absolute;
  right: 1px;
  top: 1px;
  height: 36px;
  border: 1px solid #fff;
  font-weight: bold;
  cursor: pointer;
}
.todo-item:hover > span {
  display:inline-block;
}
.dones-box{
  margin-top: 20px;
}
.done-item {
  width: 100%;
  height: 40px;
  font-size: 24px;
  line-height: 40px;
  margin-top: 10px;
  background-color: #aaaaaa;
  color: #FFF;
  position: relative;
  text-decoration: line-through;
}
</style>

<template>
  <div id="app" class="container">
    <!-- div 1 -->
    <div class="card card-body bg-light">
      <div class="title">:: Todolist App</div>
    </div>
    <!-- div 2 -->
    <div class="card card-default card-borderless">
      <div class="card-body">
        <!-- <InputTodo @add-todo="addTodo" />  컴포넌트 InputTodo기능 --> 
        <!-- <TodoList :todoList="todoList" @delete-todo="deleteTodo" @toggle-completed="toggleCompleted" />  컴포넌트 TodoList 기능 -->
        <!-- :todoList 는 data쪽 데이터 세팅 -->
        <!-- @ 는 메소드쪽 이벤트 정보세팅 -->

        <InputTodo />
        <TodoList :todoList="todoList" />
      </div>
    </div>
  </div>
</template>

<script>
  import TodoList from './components/TodoList.vue'
  import InputTodo from './components/InputTodo.vue'

  let ts = new Date().getTime()

  export default {
    name: "App",
    components : { InputTodo, TodoList },
    created() {
      this.emitter.on("add-todo", this.addTodo);
      this.emitter.on("delete-todo", this.deleteTodo);
      this.emitter.on("toggle-completed", this.toggleCompleted);
    },
    data() {
      return {
        todoList : [
          { id: ts, todo:"자전거 타기", completed: false },
          { id: ts+1, todo:"딸과 공원 산책", completed: true },
          { id: ts+2, todo:"일요일 애견 카페", completed: false },
          { id: ts+3, todo:"Vue 원고 집필", completed: false },
        ]
      }
    },
    methods: {
      // addTodo는 추가기능
      addTodo(todo) {  
        if (todo.length >= 2) {
          this.todoList.push({ id: new Date().getTime(), todo: todo, completed: false });
        }
      },
      // deleteTodo는 삭제기능
      deleteTodo(id) {
        let index = this.todoList.findIndex((item) => id === item.id);
        this.todoList.splice(index, 1);
      },
      // toggleCompleted는 클릭시 완료기능
      toggleCompleted(id) {
        let index = this.todoList.findIndex((item) => id === item.id);
        this.todoList[index].completed = !this.todoList[index].completed;
      }
    }
  }
</script>
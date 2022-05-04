<script>
// var vm = new Vue({
//   data: {
//       addNewToDo: "",
//       todos: ["clean dishes", "wash cloths", "watch tv", "learn vue"],
//       deleteEvent: function (index) {
//         this.todos.splice(index, 1);
//       },
//       editEvent: function (item, index) {
//         this.$set(this.todos,index,this.addNewToDo)

//       },
//       submit() {
//         this.todos.push(this.addNewToDo);
//       },
//     };
//   },
// })
export default {
  name: "ToDo",
  data() {
    return {
      addNewToDo: "",
      editIndex: -1,
      todos: ["clean dishes", "wash cloths", "watch tv", "learn vue"],
      deleteEvent: function (index) {
        this.todos.splice(index, 1);
      },
      editEvent: function (item, index) {
        this.addNewToDo = item;
        this.editIndex = index;
      },
      submit() {
        if (this.editIndex > -1) {
          Vue.set(this.todos, this.editIndex, this.addNewToDo);
          this.editIndex = -1;
          this.addNewToDo = "";
        } else {
          this.todos.push(this.addNewToDo);
          this.addNewToDo = "";
        }
      },
    };
  },
};
</script>
<template>
  <input v-model="addNewToDo" placeholder="ADD TODOS" />
  <button @click="submit()">submit</button>
  <h1 v-if="todos.length >= 1">TODO list:</h1>
  <ul>
    <ol v-for="(todo, index) in todos">
      <button @click="editEvent(todo, index)">EDIT</button
      >{{
        todo
      }}<button @click="deleteEvent(index)">-</button>
    </ol>
  </ul>
</template>

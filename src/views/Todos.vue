<template>
  <div class="container-xl mx-auto" style="margin: 50px 5%;">
    <!-- <h1 class="mt-8 pb-5 flex justify-center text-white text-2xl">Todos</h1> -->

    <div class="mt-3">
      <div class="grid flex flex-col-reverse sm:flex-col grid-cols-12 gap-5">
        <div class="col-span-12 md:col-span-6 2xl:mr-5" >
          <div class="p-8 bg-white rounded">
            <h2>Add a todo</h2> 
            <input type="text"
              v-model="todoText"
              @keydown.enter="addTodo"
              class="p-2 mt-4 border rounded w-full">
          </div>
        </div>
        <div class="col-span-12 md:col-span-6 space-y-4 px-1" style="height: 500px">
          <div v-for="(todo, index) in todos" :key="index" 
          class="p-8 bg-yellow-200 rounded flex items-center justify-between"
          :class="{'bg-green-50': todo.done}">
            
            <div>
              <div> {{ todo.text }} </div>
              <div class="text-gray-500 text-sm"> {{ todo.createdAt.toString() }} </div>
            </div>

            <div class="space-x-2">

              <button class="px-2 text-red-600 text-xl" 
              @click="removeTodo(index)"
              title="Remove Todo">&times;</button>

              <button v-if="!todo.done" class="px-2 text-green-600 text-l" 
              @click="markAsDone(index)"
              title="Mark as done">&check;</button>

              <button v-else class="px-2 text-yellow-800 text-l" 
              @click="markAsUndone(index)"
              title="Mark as undone">&#8630;</button>

            </div>
          </div>
          <div v-if="todos.length === 0" class="px-8 py-16 bg-yellow-100 text-gray-700 rounded text-sm">
            You don't have any tasks to do.
          </div>
        </div>

        
      </div>
    </div>
  </div>
</template>
<script>
import { defineComponent, reactive, ref } from "@vue/runtime-core"

  export default defineComponent({
    setup(){
      const todos = reactive([]);
      const todoText = ref(""); //const todoText: {values: ""}

      function addTodo(){
        todos.unshift({
          text: todoText.value,
          createdAt: new Date(),
          done: false
        })

        todoText.value = "";
      }

      function markAsDone(index){
        todos[index].done = true;     
      }

      function markAsUndone(index){
        todos[index].done = false;     
      }

      function removeTodo(index){
        if(!confirm("Are you sure?")){
          return;
        }

        todos.splice(index, 1);
      }

      return{
        todos,
        todoText,
        addTodo,
        markAsDone,
        markAsUndone,
        removeTodo,
      };  
    }
  })
</script>


        // {
        //   text: 'First Todo',
        //   createdAt: new Date(),
        //   done: false,
        // },
      
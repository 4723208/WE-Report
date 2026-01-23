# 第14回 Webエンジニアリング演習 レポート
## 学籍番号(名前は書かなくてよい)
4723208
## 実装した内容

index.ts
```ts
import { createRouter, createWebHistory } from 'vue-router'
import TodoListView from '../views/TodoListView.vue' 
import About from '../views/About.vue'
import TodoDetail from '../views/TodoDetail.vue' 

const routes = [ 
    { path: '/' , name: 'TodoList' , component: TodoListView },
    { path: '/todos' , name: 'TodoList' , component: TodoListView },
    { path: '/about', name:'About', component: About },
    { path: '/todos/:id', name:'Detail', component: TodoDetail}
 ] 

 
export const router = createRouter({ 
    history: createWebHistory(), 
    routes 
}) 

export default router
```



TodoDetail.vue
```ts
<script setup lang="ts">
import { useRoute } from 'vue-router';
import { useTodoStore } from '../stores/todoStores';
const todoStore = useTodoStore()
const route = useRoute()
const id = Number(route.params.id)

</script>

<template>
    <section>
        <h2>Todo Details</h2>
        <div v-if="todoStore.todos[id - 1]">
        {{ todoStore.todos[id-1] }}
        </div>
    </section>
</template>
```


TodoListView.vue
```ts
<script setup lang="ts">

import AddTodo from '../components/AddTodo.vue';
import { useTodoStore } from '../stores/todoStores';


import { ref, computed } from 'vue';
const name = ref('Vue 3 with TypeScript');

const todoStore = useTodoStore();


</script>

<template>
  <section>

    <h2>Todos</h2>

    <ul>
      <li
        v-for="todo in todoStore.todos"
        :key="todo.id"
        style="display:flex; align-items:center; gap:0.5rem; margin:0.25rem 0;"
      >
        <input type="checkbox" v-model="todo.completed" />
        <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }"><router-link :to="`/todos/` + todo.id">
            {{ todo.title }}
        </router-link>
        </span>
        <button v-on:click="todoStore.removeTodo(todo.id)">Delete</button>
      </li>
    </ul>


  </section>

  <section>
       <AddTodo /> 
  </section>



</template>

```
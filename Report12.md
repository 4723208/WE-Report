# 第12回 Webエンジニアリング演習 レポート
## 学籍番号(名前は書かなくてよい)
4723208

## 本日の感想
TypeScriptの型のついて理解が足りていなかったため、エラーの解消に時間がかかった。
componentの概念ついては理解できたが、双方方向バインディングについては頭が少々混乱した。

## 実装したコード
App.vue
```ts
<script setup lang="ts">
import AddTodo from './components/AddTodo.vue';

import { ListFormat } from 'typescript';
import { ref, computed } from 'vue';
const name = ref('Vue 3 with TypeScript');

type Todo = { id: number; title: string; completed: boolean };

const todos = ref<Todo[]>([
  { id: 1, title: 'Buy groceries', completed: false},
  { id: 2, title: 'Write report', completed: true },
  { id: 3, title: 'Call Alice', completed: false },  
]);

const falseTodos = computed(() => todos.value.filter((i) => i.completed === false));
const falseTodosValue = computed(() => falseTodos.value.length);





</script>

<template>
  <div id="app">
    <h2>Todos({{ falseTodosValue }})</h2>

    <ul>
      <li
        v-for="todo in todos"
        :key="todo.id"
        style="display:flex; align-items:center; gap:0.5rem; margin:0.25rem 0;"
      >
        <input type="checkbox" v-model="todo.completed" />
        <span :style="{ textDecoration: todo.completed ? 'line-through' : 'none' }">
          {{ todo.title }}
        </span>
      </li>
    </ul>

    <AddTodo v-model:todos="todos" />

  </div>
</template>
```

AddTodo.vue
```ts
<script setup lang="ts">  
import { ref } from 'vue';

type Todo = {id: number; title: string; completed: boolean };

const todos = defineModel<Todo[]>("todos", {required: true});



const newTitle = ref('');

const nextId = ref(Math.max(0, ...todos.value.map((t) => t.id)) + 1);

function addTodo() {
  const title = newTitle.value;
  todos.value.push({ id: nextId.value++, title, completed: false });
  newTitle.value = '';
}
</script>

<template>
  <section>
    <h2>New todo</h2>
    <div style="display: flex; align-items: center; gap: 0.5rem; margin-top: 0.25rem;">
      <input
       v-model="newTitle"
       placeholder="New todo title"
       aria-label="=New todo title"
      />
      <button v-on:click="addTodo" :disabled="!newTitle">Add</button>
    </div>
  </section>

</template>
```
# 第10回 Webエンジニアリング演習 レポート
## 学籍番号(名前は書かなくてよい)
4723208
## 実装したコード

```ts
<script setup lang="ts">
  import { ref } from 'vue'
  const name = ref('John Doe')

  function changeName() {
    if (name.value === 'John Doe') {
      name.value = '自分の名前'
    } else {
      name.value = 'John Doe'
    }
  }

  setInterval(changeName, 2000)


</script>

<template>
  <div>
    <p>Hello, <span class="name">{{ name }}</span>!</p>
  </div>
</template>

<style scoped>
.name {
  color: #9acd32; /* yellowgreen */
}
</style>
```

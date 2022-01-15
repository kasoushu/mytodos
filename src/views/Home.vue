<template>
  <div class="home">
    <my-todo></my-todo>
  </div>
</template>

<script>
// @ is an alias to /src
import myTodo from '@/components/myTodo'

export default {
  name: 'Home',
  components: {
    myTodo
  }
}
</script>

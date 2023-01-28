<template>
  <v-app>
    <v-app-bar title="TodoList"></v-app-bar>
    <v-main>
      <TodoList />
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoList from "./views/todo/TodoList.vue";

export default defineComponent({
  name: "App",

  components: {
    TodoList,
  },

  data() {
    return {
      //
    };
  },
});
</script>

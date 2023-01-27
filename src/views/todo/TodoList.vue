<template>
  <v-container>
    <TodoListWrap :Todolists="Todolists" />
    <v-btn
      class="floating"
      icon="mdi-pencil"
      size="small"
      @click="showDialog()"
    />
    <v-dialog v-model="dialog">
      <TodoListWrite
        :dialog="dialog"
        :edit="edit"
        @hideTodo="hideDialog()"
        @submitTodo="submitDialog()"
      />
    </v-dialog>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoListWrap from "./TodoListWrap.vue";
import TodoListWrite from "./TodoListWrite.vue";

interface ITodoLists {
  title: string;
  contents: string;
  checked: boolean;
}

export default defineComponent({
  name: "TodoList",
  components: {
    TodoListWrap,
    TodoListWrite,
  },
  data() {
    return {
      dialog: false,
      edit: false,
      Todolists: [
        { title: "제목이야", contents: "sss", checked: true },
      ] as ITodoLists[],
    };
  },
  methods: {
    showDialog() {
      this.dialog = true;
    },
    hideDialog() {
      console.log("sss");
      this.dialog = false;
    },
    submitDialog(title: string, contents: string) {
      console.log("submit 완료!", title, contents);
      this.dialog = false;
    },
  },
});
</script>

<style lang="scss" scoped>
.floating {
  position: fixed;
  right: 24px;
  bottom: 24px;
}
</style>

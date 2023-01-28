<template>
  <v-container>
    <TodoListWrap
      :Todolists="Todolists"
      @isChecked="isChecked"
      @deleteTodo="deleteTodo"
      @showDialog="showDialog"
    />
    <v-btn
      class="floating"
      icon="mdi-pencil"
      size="small"
      @click="showDialog()"
    />
    <v-dialog v-model="dialog">
      <TodoListWrite
        :dialog="dialog"
        :edits="edits"
        :editTodo="edits.edit ? Todolists[edits.idx] : {}"
        @hideDialog="hideDialog"
        @submitDialog="submitDialog"
        @editSubmitDialog="editSubmitDialog"
      />
    </v-dialog>
  </v-container>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoListWrap from "./TodoListWrap.vue";
import TodoListWrite from "./TodoListWrite.vue";

interface ITodoLists {
  id: Number;
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
      edits: {
        idx: 0,
        edit: false,
      },
      Todolists: [
        { id: 1, title: "제목이야", contents: "sss", checked: true },
      ] as ITodoLists[],
    };
  },
  methods: {
    showDialog(idx?: number) {
      this.dialog = true;
      if (idx !== undefined) {
        this.edits.idx = idx;
        this.edits.edit = true;
      } else {
        this.edits.idx = 0;
        this.edits.edit = false;
      }
    },
    hideDialog() {
      this.dialog = false;
    },
    submitDialog(todos: ITodoLists) {
      console.log("submit 완료!", todos, this.Todolists.length + 1);
      const TodoItem = {
        ...todos,
        id: this.Todolists.length + 1,
      };
      this.Todolists.push(TodoItem);
      this.dialog = false;
    },
    editSubmitDialog(todos: ITodoLists) {
      console.log("submit 수정!", todos, this.Todolists.length + 1);
      const TodoItem = {
        ...todos,
      };
      this.Todolists[this.edits.idx] = TodoItem;
      this.dialog = false;
    },
    isChecked(idx: number) {
      console.log("asss", idx);
      this.Todolists[idx].checked = !this.Todolists[idx].checked;
    },
    deleteTodo(idx: number) {
      console.log("asss", idx);
      this.Todolists.splice(idx, 1);
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

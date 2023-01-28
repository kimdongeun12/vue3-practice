<template>
  <v-card>
    <v-card-title>
      {{ $props.edits?.edit ? "수정하기" : "등록하기" }}
    </v-card-title>
    <v-card-text>
      <div>
        <v-text-field label="제목" v-model="todos.title"></v-text-field>
        <v-text-field label="내용" v-model="todos.contents"></v-text-field>
      </div>
    </v-card-text>
    <v-card-actions class="justify-end">
      <v-btn color="primary" variant="text" @click="$emit('hideDialog')">
        닫기
      </v-btn>
      <v-btn color="primary" variant="text" @click="onClickSubmit()">
        저장
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "TodoListWrite",
  emits: ["hideDialog", "submitDialog", "editSubmitDialog"],
  components: {},
  props: {
    edits: Object,
    editTodo: Object,
  },
  data() {
    return {
      todos: {
        title: "",
        contents: "",
        checked: false,
      },
    };
  },
  created() {
    console.log(this.editTodo);
    this.todos.title = this.editTodo?.title;
    this.todos.contents = this.editTodo?.contents;
    this.todos.checked = this.editTodo?.checked;
  },
  methods: {
    onClickSubmit() {
      if (!this.todos.title) {
        alert("제목을 입력해주세요.");
        return;
      }
      if (!this.todos.contents) {
        alert("내용을 입력해주세요.");
        return;
      }
      if (this.edits?.edit) {
        this.$emit("editSubmitDialog", this.todos);
      } else {
        this.$emit("submitDialog", this.todos);
      }
    },
  },
});
</script>

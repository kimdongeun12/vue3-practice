<template>
  <v-card>
    <v-card-title> {{ $props.edit ? "수정하기" : "등록하기" }} </v-card-title>
    <v-card-text>
      <div>
        <v-text-field label="제목"></v-text-field>
        <v-text-field label="내용"></v-text-field>
      </div>
    </v-card-text>
    <v-card-actions class="justify-end">
      <v-btn color="primary" variant="text" @click="$emit('hideTodo')">
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
  emits: ["hideTodo", "submitTodo"],
  components: {},
  props: {
    edit: Boolean,
  },
  data() {
    return {};
  },
  methods: {
    onClickSubmit() {
      this.$emit("submitTodo", "aaa", "bbb");
    },
  },
});
</script>

<template>
  <div class="listsWrap">
    <v-card
      class="mx-auto my-list"
      v-for="(item, idx) in Todolists"
      :key="idx"
      :class="{ 'mx-auto active': item?.checked }"
      width="400"
    >
      <template v-slot:title>
        <v-btn
          variant="text"
          icon="mdi-check"
          size="small"
          @click="$emit('isChecked', idx)"
        />
        {{ item?.title }}
      </template>

      <v-card-text> {{ item?.contents }} </v-card-text>
      <v-card-actions class="justify-end">
        <v-btn variant="outlined" @click="$emit('showDialog', idx)">
          수정
        </v-btn>
        <v-btn variant="outlined" @click="$emit('deleteTodo', idx)">
          삭제
        </v-btn>
      </v-card-actions>
    </v-card>
    <div class="text-center" v-if="Todolists?.length === 0">
      할 일 목록이 없습니다.<br />
      우측 아래 버튼을 클릭하여 추가해주세요.
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "TodoListWrap",
  components: {},
  props: {
    Todolists: Object,
  },
  data() {
    return {};
  },
});
</script>
<style lang="scss" scoped>
.listsWrap {
  display: block;
  & > div + div {
    margin-top: 20px;
  }
  .active:deep .v-card-title .v-btn__content {
    color: #ff0000;
  }
}
</style>

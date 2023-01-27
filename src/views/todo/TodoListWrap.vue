<template>
  <div class="listsWrap">
    <ListItem01 v-for="(item, idx) in Todolists" :key="idx" :item="item" />
    <div class="text-center" v-if="Todolists?.length === 0">
      할 일 목록이 없습니다.<br />
      우측 아래 버튼을 클릭하여 추가해주세요.
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ListItem01 from "@/components/list/ListItem01.vue";

export default defineComponent({
  name: "TodoListWrap",
  components: {
    ListItem01,
  },
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
}
</style>

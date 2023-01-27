<template>
  <v-card
    class="mx-auto my-list"
    :class="{ 'mx-auto active': item?.checked }"
    width="400"
    prepend-icon="mdi-check"
  >
    <template v-slot:title> {{ item?.title }} </template>

    <v-card-text> {{ item?.contents }} </v-card-text>
  </v-card>
  <!-- <li>{{ item }}</li> -->
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ListItem01",

  props: {
    item: Object,
  },
  data() {
    return {};
  },
});
</script>
<style scoped>
.active:deep .v-avatar {
  color: #ff0000;
}
</style>

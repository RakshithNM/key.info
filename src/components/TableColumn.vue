<template>
  <div class="tableColumn">
    <p>{{title}}</p>
    <h1>{{ item }}</h1>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
  name: 'TableColumn',
  props: {
    item: [String, Number],
    title: String 
  },
  setup: () => {
  },
})
</script>

<style scoped>
.tableColumn {
    border-radius: 4px;
    border: 1px solid orangered;
}

p {
    margin: 0;
    background-color: darkslategray;
    color: white;
}

h1 {
  color: red;
}
</style>

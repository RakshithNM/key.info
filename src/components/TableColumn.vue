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
  cursor: pointer;
}

.tableColumn:hover {
  transform: translateY(-10px);
  transition: transform 0.3s ease-in;
  box-shadow: 0 14px 26px rgb(158 156 156 / 40%);
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

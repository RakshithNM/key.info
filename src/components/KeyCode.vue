<template>
  <main>
    <h1 class="title" :class="{largefontsize: isLargeFont, smallfontsize: !isLargeFont}">{{ title }}</h1>
    <section v-if="keyPressed">
      <h1 class="keycode">{{ keyEvent.keyCode }}</h1>
      <div class="table">
        <TableColumn :item="keyEvent.key" title="event.key" />
        <TableColumn :item="keyEvent.keyLocation" title="event.location" />
        <TableColumn :item="keyEvent.keyWhich" title="event.which" />
        <TableColumn :item="keyEvent.keyName" title="event.code" />
      </div>
    </section>
    <p v-if="!keyPressed">Press any key to get the Javascript event keycode</p>
  </main>
</template>

<script lang="ts">
import { ref, defineComponent, onMounted, computed } from 'vue'
import TableColumn from "./TableColumn.vue"
export default defineComponent({
  name: 'KeyCode',
  props: {
    title: {
      type: String,
      required: true
    }
  },
  components: {
    TableColumn
  },
  setup: () => {
    let keyEvent = ref({
      keyCode : -1,
      key: "",
      keyLocation: -1,
      keyWhich: -1,
      keyName: ""
    })
    let keyPressed = ref(false);
    onMounted(() => {
      window.addEventListener("keydown", e => {
        keyPressed.value = true
        console.log(e);
        keyEvent.value = {
          key: e.key,
          keyCode: e.keyCode,
          keyWhich: e.which,
          keyLocation: e.location,
          keyName: e.code
        } 
      });
    })
    const isLargeFont = computed(() => keyPressed.value === false);
    return {
      keyEvent,
      keyPressed,
      isLargeFont
    }
  },
})
</script>

<style scoped>
.keycode {
  margin: 0;
  font-size: 40vmin;
  color: limegreen;
}

.title {
  margin-bottom: 0;
}

.largefontsize {
  font-size: 20vmin;
}

.smallfontsize {
  font-size: 10vmin;
}

.table {
  --min: 10ch;
  --gap: 1rem;

  display: flex;
  width: clamp(80%, 85%, 90%);
  flex-direction: row;
  margin: auto;
  flex-wrap: wrap;
  gap: var(--gap);
}

.table > * {
  flex: 1 1 var(--min);
}
</style>

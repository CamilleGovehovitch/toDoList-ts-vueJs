<template>
  <div class="main">
    <button>{{ buttonContent }}</button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'createButton',
  data() {
    return {
      buttonContent: 'Add Card'
    }
  }
})
</script>

<style scoped>
.main {
  background-color: darkgray;
  width: 100vw;
  padding: 0 20px 5px 20px;
  text-align: end;
  button {
    font-size: 16px;
    text-align: end;
    color: black;
  }
}
</style>

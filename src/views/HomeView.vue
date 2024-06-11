<template>
  <main class="mainContainer">
    <appHeader :title="title" />
    <CreateButton />
    <div class="taskManager">
      <appCard />
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import appHeader from '../components/appHeader.vue'
import CreateButton from '../components/CreateButton.vue'
import appCard from '../components/appCard.vue'

const title = ref<string>('Task ManagerZ')
</script>
<style scoped lang="scss">
.mainContainer {
  height: 100vh;
  width: 100vw;
  .taskManager {
    padding: 20px;
    overflow: scroll;
    background-color: darkgray;
    border: solid 20px darkgray;
    height: calc(100vh - 100px);
  }
}
</style>

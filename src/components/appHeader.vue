<template>
  <div class="main">
    <h1>{{ title }}</h1>
    <div class="informationOfTheDay">
      <span id="">{{ dateOfTheDay }}</span>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

//Define reactive variables
// const title = ref<string>('Task Manager')
let dateOfTheDay = ref<string>('')

const props = defineProps({
  title: String
})

onMounted(() => {
  displayDate()
})
// funtion to display the date
const displayDate: () => void = () => {
  let date: Date = new Date()
  let year: number = date.getFullYear()
  let month: number = date.getMonth() + 1
  let day: number = date.getDay()

  let formatedDay: string = day < 10 ? '0' + day.toString() : day.toString()
  let formatedMonth: string = month < 10 ? '0' + month.toString() : month.toString()

  dateOfTheDay.value = `${formatedDay}/${formatedMonth}/${year}`
}
</script>

<style scoped lang="scss">
.main {
  background-color: darkgray;
  padding: 0;
  width: 100vw;
  text-align: center;
  h1 {
    color: black;
    font-size: 24px;
    padding: 15px;
  }
  .informationOfTheDay {
    font-size: 12px;
  }
}
</style>

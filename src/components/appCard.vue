<template>
  <div class="card">
    <div class="cardTitle new">
      <div class="title">
        <div>
          <h1>{{ title.content }}</h1>
        </div>
        <div class="titlePanelControl">
          <img src="../assets/img/valide.png" alt="" class="icons" @click="title.checked = true" />
          <img src="../assets/img/editer.png" alt="" class="icons" @click="title.checked = false" />
        </div>
        <input type="text" v-model="title.content" v-if="title.checked === false" />
      </div>
      <div class="addTask">
        <button @click="createTask">Add Task</button>
      </div>
    </div>
    <div class="content" id="taskManager">
      <div class="task" v-for="(task, index) in tasks" :key="index">
        <div class="taskChecked">
          <input type="checkbox" v-model="task.checked" />
        </div>
        <input type="text" v-model="task.content" />
        <div class="taskControlls">
          <img src="../assets/img/valide.png" alt="" class="icons" />
          <img src="../assets/img/editer.png" alt="" class="icons" />
          <img src="../assets/img/supprimer.png" alt="" class="icons" @click="deleteTask(index)" />
        </div>
      </div>
    </div>
    <div class="filterPriority">
      <select name="" id="">
        <option value="">New</option>
        <option value="">WIP</option>
        <option value="">Finished</option>
      </select>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'

interface Title {
  content: string
  checked: boolean
}

interface Task {
  content: string
  checked: boolean
}

const title = ref<Title>({ content: '', checked: false })
const tasks = ref<Task[]>([])

function createTask(): void {
  tasks.value.push({
    content: '',
    checked: false
  })
}

function deleteTask(index: number): void {
  tasks.value.splice(index, 1)
}
</script>
<style lang="scss">
.card {
  width: 300px;
  height: 400px;
  background-color: whitesmoke;
  border-radius: 5px;
  .cardTitle {
    height: 30%;
    border-bottom: solid 1px black;
    .title {
      text-align: center;
      h1 {
        padding: 5px 0px 5px 0px;
        text-align: center;
      }
    }
    .titlePanelControl {
      img {
        width: 20px;
        margin: 0px 5px 0px 5px;
      }
    }
    .addTask {
      text-align: end;
      padding-right: 5px;
      button {
        border: 0px;
      }
    }
  }
  .content {
    height: 60%;
    text-align: center;
    padding: 5px;
    overflow: scroll;
    .task {
      display: flex;
      align-items: center;
      justify-content: space-between;
      .taskChecked {
        width: 10%;
      }
      input {
        width: 60%;
        border: 0;
        border-radius: 5px;
        margin-bottom: 5px;
      }
      .taskControlls {
        width: 30%;
        margin: 0px 5px 0px 5px;
        .icons {
          width: 20px;
          margin-right: 5px;
        }
      }
    }
  }
  .filterPriority {
    padding: 5px 10px;
    height: 10%;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
    select {
    }
  }
}
.new {
  background-color: lightblue;
}
</style>

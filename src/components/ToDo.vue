<template>
  <div>
    <div v-for="(item, index) in items" :key="item.title">
      <ToDoCard :item="item" @complete="deleteTask(index)" />
    </div>
    <Dialog @submit="addTask()" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ToDoCard from "./ToDoCard.vue";
import Dialog from "./Dialog.vue";
import Task from "../Task";

@Component({
  components: {
    ToDoCard,
    Dialog
  }
})
export default class ToDo extends Vue {
  public items: Task[] = [
    {
      title: "物理学演習",
      detail: "プリントの中から2題",
      date: "2019-11-14",
      done: false
    },
    {
      title: "物理学実験",
      detail: "実験計画書",
      date: "2019-11-14",
      done: false
    }
  ];
  public addTask(item: Task) {
    this.items.push(item);
  }
  public deleteTask(i: number) {
    this.items.splice(i, 1);
  }
}
</script>

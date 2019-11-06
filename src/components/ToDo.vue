<template>
  <div>
    <div v-for="item in items" :key="item.id">
      <ToDoCard :item=item />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ToDoCard from "./ToDoCard.vue"

@Component({
  components:{
    ToDoCard
  }
})

export default class ToDo extends Vue {
  public items: {
    id: number;
    name: string;
    detail: string;
    date: string;
    done: boolean;
  }[] = [
    { id: 1, 
    name: "物理学演習",
    detail: "プリントの中から2題" ,
    date: "2019-11-14",
    done: false},
    { id: 2, 
    name: "物理学実験",
    detail: "実験計画書",
    date: "2019-11-14",
    done: false}
  ];
  newItemName: string = "";
  newItemDetail: string = "";
  newItemDate: string = "";
}
</script>

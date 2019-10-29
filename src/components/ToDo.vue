<template>
   <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Name</th>
          <th class="text-left">Detail</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.name">
          <td>{{ item.name }}</td>
          <td>{{ item.detail }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script lang = "ts">
import { Component, Vue } from 'vue-property-decorator';

@Component
export default class ToDo extends Vue {
  items: {name: string, detail:string }[] = [
      {name: "物理学演習", detail: "プリントの中から2題"},
      {name: "物理学実験", detail: "実験計画書"},
  ];
  newItemName: string = "";
  newItemDetail: string = "";
}
</script>
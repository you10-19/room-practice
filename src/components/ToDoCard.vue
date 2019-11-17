<template>
  <v-card outlined>
    <v-container>
      <v-row no-gutters>
        <v-icon>event</v-icon>
        <v-list>
          <v-subheader>>{{ item.date }}</v-subheader>
          <v-list-item-content two-line>
            <v-list-title>{{ item.title }}</v-list-title>
            <v-list-subtitle>{{ item.detail }}</v-list-subtitle>
          </v-list-item-content>
        </v-list>
        <v-card-actions>
          <v-btn v-if="item.done" text @click="item.done = false"
            >元に戻す</v-btn
          >
          <v-btn v-else text @click="complete">完了済みにする</v-btn>
        </v-card-actions>
      </v-row>
    </v-container>
  </v-card>
</template>

<script lang="ts">
import { Component, Prop, Emit, Vue } from "vue-property-decorator";
import Task from "../Task";

@Component
export default class ToDoCard extends Vue {
  @Prop()
  public item!: Task;

  @Emit("complete")
  complete() {}
}
</script>

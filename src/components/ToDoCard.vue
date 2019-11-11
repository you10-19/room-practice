<template>
  <v-card outlined>
    <v-container>
      <v-row>
        <v-icon>event</v-icon>
        <!-- v-iconを使えるようにする -->
        <v-col align-start>
          <v-card-title>{{ item.title }}</v-card-title>
          <v-card-subtitle>{{ item.detail }}</v-card-subtitle>
          <v-card-text>{{ item.date }}</v-card-text>
          <v-card-actions>
            <v-btn v-if="item.done" text @click="item.done = false"
              >元に戻す</v-btn
            >
            <v-btn v-else text @click="complete">完了済みにする</v-btn>
          </v-card-actions>
        </v-col>
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

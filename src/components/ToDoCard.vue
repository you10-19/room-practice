<template>
  <v-card outlined>
    <v-container>
      <v-row>
        <v-icon>event</v-icon>
        <v-col>
          <v-card-title>{{item.name}}</v-card-title>
          <v-card-subtitle>{{item.detail}}</v-card-subtitle>
          <v-card-actions>
            <v-btn v-if="item.done" text>元に戻す</v-btn>
            <v-btn v-else text>変更する</v-btn>
          </v-card-actions>
          <v-card-actions>
            <v-btn v-if="item.done" text>削除する</v-btn>
            <v-btn v-else text>完了済みにする</v-btn>
          </v-card-actions>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class ToDoCard extends Vue {
  @Prop()
  item?:{
      name: string,
      detail: string,
      date: string,
      done: boolean
  };
}
</script>
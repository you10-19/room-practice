<template>
  <v-card outlined>
    <v-container>
      <v-row>
        <v-icon>home</v-icon>
        <v-col>
          <v-card-title>{{item.name}}</v-card-title>
          <v-card-subtitle>{{item.detail}}</v-card-subtitle>
          <v-card-text>{{item.date}}</v-card-text>
          <v-card-actions>
            <v-btn v-if="item.done" text @click="revaival()">元に戻す</v-btn>
            <v-btn v-else text @click="finish()">完了済みにする</v-btn>
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
  public item!:{
      name: string,
      detail: string,
      date: string,
      done: boolean,
  };

  public revaival(){
      this.item.done = false;
  };

  public finish(){
      this.item.done = true;
  };
}
</script>
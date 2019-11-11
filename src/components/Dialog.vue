<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" max-width="600px">
      <template v-slot:activator="{ on }">
        <v-btn color="primary" dark v-on="on">追加する</v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span>新しいタスク</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="4">
                <v-form>
                  <v-text-field
                  label="title"
                  placeholder="新しいタスク"
                  v-model="newItem.title"
                  required
                  >
                  </v-text-field>
                  <v-text-field
                  label="detail"
                  placeholder="詳細"
                  v-model="newItem.detail"
                  >
                  </v-text-field>
                  <v-text-field
                  label="date"
                  placeholder="期日"
                  v-model="newItem.date"
                  >
                 </v-text-field>
                </v-form>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="onclick">追加する</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script lang="ts">
import { Component, Prop, Emit, Vue } from "vue-property-decorator";
import Task from "../Task";

@Component
export default class Dialog extends Vue {
  public dialog: boolean = false;
  public newItem: Task ={
      title: "",
      detail: "",
      date: "",
      done: false
  }
  
  @Emit("submit")
  onclick() {
    return this.newItem
  }
}
</script>

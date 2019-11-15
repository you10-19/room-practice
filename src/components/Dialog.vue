<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" max-width="600px">
      <template v-slot:activator="{ on }">
        <v-btn color="primary" dark v-on="on" @click="clear">追加する</v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span>新しいタスク</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12" sm="6" md="4">
                <v-form ref="form">
                  <v-text-field
                    label="title"
                    placeholder="新しいタスク"
                    v-model="newItemTitle"
                    required
                  >
                  </v-text-field>
                  <v-text-field
                    label="detail"
                    placeholder="詳細"
                    v-model="newItemDetail"
                  >
                  </v-text-field>
                  <v-text-field
                    label="date"
                    placeholder="期日"
                    v-model="newItemDate"
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
  public valid: boolean = true;
  public newItemTitle: string = "";
  public newItemDetail: string = "";
  public newItemDate: string = ""; 
  public clear() {
    if (this.$refs.form){
      this.form.reset();
    }
  }
  @Emit("submit")
  onclick(): Task {
    this.dialog = false;
    return {
      title: this.newItemTitle,
      detail: this.newItemDetail,
      date: this.newItewmDate,
      done: false
    };
  }

  get form(): Vue & { reset: () => void } {
    return this.$refs.form as Vue & { reset: () => void };
  }
}
</script>

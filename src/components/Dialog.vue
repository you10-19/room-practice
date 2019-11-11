<template>
<v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="600px">
        <template v-slot:activator="{ on }">
          <v-btn color="primary" dark v-on="on">追加する</v-btn>
        </template>
        <v-card>
          <v-card-text>
            <v-container>
              <v-row>
                <v-col cols="12" sm="6" md="4">
                  <v-text-field 
                  label="title" 
                  placeholder="新しいタスク" 
                  v-model="newItemTitle" 
                  required>
                  </v-text-field>
                  <v-text-field 
                  label="detail" 
                  placeholder="詳細"
                  v-model="newItemDetail"
                  >
                  </v-text-field>
                </v-col>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="onclick()">追加する</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
import Task from "../Task";

@Component
export default class Dialog extends Vue {
    @Prop()
    public newItem?: Task;
    public onclick(){
        this.$emit("submit", this.newItem);
    }
}
</script>
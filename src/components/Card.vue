<template>
  <v-dialog
      v-model="dialog"
      max-width="500px"
  >
    <template v-slot:activator="{ on }">
      <v-card v-on="on" tile class="inside-card">
        <v-card-title>{{ task.title }}</v-card-title>
        <v-card-text>{{ task.desc }}</v-card-text>
      </v-card>
    </template>
    <v-card>
      <v-card-title>
        <v-col cols="9" class="float-left" justify="left">
          {{ task.title }}
        </v-col>
        <v-col cols="3">
          <v-tooltip bottom v-if="isLast !== true">
            <template v-slot:activator="{ on }">
              <v-icon @click="upgrade" v-on="on" style="cursor: pointer;">mdi-arrow-up-box</v-icon>
            </template>
            <span>Upgrade la tâche</span>
          </v-tooltip>
          <v-tooltip bottom>
            <template v-slot:activator="{ on }">
              <v-icon @click="deleteTask" v-on="on" style="cursor: pointer;">mdi-delete</v-icon>
            </template>
            <span>Supprimer la tâche</span>
          </v-tooltip>
        </v-col>
      </v-card-title>
      <v-divider></v-divider>
      <v-card-text style="margin-top: 15px !important;">{{ task.desc }}</v-card-text>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn
            color="blue darken-1"
            text
            @click="dialog = false"
        >
          Annuler
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: "Card",

  props: ['task', 'isLast', 'currentState', 'nextState', 'index'],

  data: () => ({
    dialog: false,
  }),

  methods: {
    upgrade() {
      const item = {
        id: this.task.id,
        title: this.task.title,
        desc: this.task.desc
      };
      this.nextState.push(item);
      this.deleteTask();
      this.dialog = false;
    },
    deleteTask() {
      for (let task of this.currentState) {
        console.log(task.id === this.task.id);
         if (task.id === this.task.id) {
           const index = this.currentState.indexOf(task);
           this.currentState.splice(index, 1);
         }
      }
    }
  }
}
</script>
<template>
    <v-dialog
        v-model="dialog"
        max-width="600px"
    >
      <template v-slot:activator="{ on }">
      <v-btn
          slot="activator"
          v-on="on"
          width="100%"
      >
        <svg style="width:24px;height:24px" viewBox="0 0 24 24">
          <path fill="currentColor" d="M20 14H14V20H10V14H4V10H10V4H14V10H20V14Z" />
        </svg>
      </v-btn>
      </template>
      <v-card>
        <v-card-title>
          <span class="headline">Créer une nouvelle tâche</span>
        </v-card-title>
        <v-card-text>
          <v-container>
            <v-row>
              <v-col cols="12">
                <v-text-field label="Titre de la tâche" required v-model="taskTitle"></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12">
                <v-textarea label="Description de la tâche" counter="60" required v-model="taskDesc"></v-textarea>
              </v-col>
            </v-row>
          </v-container>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
              color="blue darken-1"
              text
              @click="dialog = false"
          >
            Annuler
          </v-btn>
          <v-btn
              color="blue darken-1"
              text
              @click="validate"
          >
            Sauvegarder
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</template>

<script>
export default {
  name: "AddTask",
  props: ['todo', 'index'],

  data: () => ({
    dialog: false,
    taskTitle: "",
    taskDesc: "",
  }),

  methods: {
    validate() {
      if (this.taskTitle.length > 0 && this.taskDesc.length > 0) {
        const item = {id: this.index+1, title: this.taskTitle, desc: this.taskDesc}
        this.index++;
        this.todo.push(item);
        this.dialog = false;
      }
    }
  }

}
</script>

<style scoped>

</style>
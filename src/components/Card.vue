<template>
  <v-dialog
      v-model="dialog"
      max-width="600px"
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
              <v-icon v-on="on" style="cursor: pointer;" >mdi-arrow-up-box</v-icon>
            </template>
            <span>Upgrade la tâche</span>
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

  props: ['task', 'isLast'],

  data: () => ({
    dialog: false,
  }),
}
</script>
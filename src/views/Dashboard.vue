<template>
  <v-container>
    <v-row class="justify-center title-wrapper">
      <v-col cols="12">
        <h1>Mon projet</h1>
      </v-col>
    </v-row>
    <v-divider></v-divider>
    <v-row class="col-area text-center">
      <v-col cols="3">
        <h2 style="margin-bottom: 15px;">À faire</h2>
        <div data-app>
          <AddTask/>
        </div>
        <v-card tile class="inside-card">
          <v-card-title>Title</v-card-title>
          <v-card-text>Text</v-card-text>
        </v-card>
        <v-card tile class="inside-card">
          <v-card-title>Title</v-card-title>
          <v-card-text>Text</v-card-text>
        </v-card>
      </v-col>
      <v-col cols="1"></v-col>
      <v-col cols="3">
        Test
      </v-col>
      <v-col cols="1"></v-col>
      <v-col cols="3">
        Test
      </v-col>

    </v-row>
  </v-container>
</template>

<script>
import AddTask from "@/components/AddTask";
export default {
  name: "Dashboard",

  data: () => ({
    dialog: false,
  }),

  components: {
    AddTask,
  }
}
</script>

<style scoped>

</style>
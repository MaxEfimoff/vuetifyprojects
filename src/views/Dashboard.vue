<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>

    <v-container class="my-5">
      <v-layout row class="mb-3 ml-2">
        <v-btn @click="sortBy('title')" small text color="grey">
          <v-icon left small>mdi-folder</v-icon>
          <span class="caption text-lowercase">By Project name</span>
        </v-btn>
        <v-btn @click="sortBy('person')" small text color="grey">
          <v-icon left small>mdi-account</v-icon>
          <span class="caption text-lowercase">By Person</span>
        </v-btn>
      </v-layout>
      <v-card v-for="project in projects" :key="project.title" row :class="`pa-3 project ${project.status}`">
        <v-layout>
          <v-flex xs12 md6>
            <div class="caption grey--text">Project Title</div>
            <div>{{ project.title }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Person</div>
            <div>{{ project.person }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Due Date</div>
            <div>{{ project.due }}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="right">
              <v-chip small :class="`${project.status} white--text caption my-2`">{{ project.status }}</v-chip>
            </div>
          </v-flex>
        </v-layout>
        <!-- <v-divider /> -->
      </v-card>
    </v-container>

  </div>
</template>

<script>

export default {
  data() {
    return {
      projects: [
        {title: 'Design front page', person: 'Max Efi', due: '01/01/2020', status: 'complete'},
        {title: 'Design backend', person: 'Dan Myers', due: '16/02/2020', status: 'overdue'},
        {title: 'Design video thumbinals', person: 'Jhon Doe', due: '12/03/2020', status: 'ongoing'},
        {title: 'Create forum', person: 'Max Efi', due: '01/03/2020', status: 'ongoing'},
      ]
    }
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
};
</script>

<style scoped>
.project.complete{
  border-left: 4px solid #3cd1c2;
}
.project.ongoing{
  border-left: 4px solid orange;
}
.project.overdue{
  border-left: 4px solid tomato;
}
.v-chip.cpmplete{
  background: #3cd1c2;
}
.v-chip.ongoing{
  background: #ffaa2c;
}
.v-chip.overdue{
  background: #f83e70;
}
</style>
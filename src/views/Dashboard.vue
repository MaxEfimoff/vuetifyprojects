<template>
  <div class="dashboard">
    <h1 class="subheading grey--text">Dashboard</h1>

    <v-container class="my-5">
      <v-layout row class="mb-3 ml-2">
        <v-btn @click="sortBy('title')" small text color="grey">
          <v-icon left small>mdi-folder</v-icon>
          <span class="caption text-lowercase">By Project name</span>
          <v-icon left small class="ml-1" v-if="this.isAscendingTitle === false">mdi-chevron-down</v-icon>
          <v-icon left small class="ml-1" v-if="this.isAscendingTitle === true">mdi-chevron-up</v-icon>
        </v-btn>
        <v-btn @click="sortBy('person')" small text color="grey">
          <v-icon left small>mdi-account</v-icon>
          <span class="caption text-lowercase">By Person</span>
          <v-icon left small class="ml-1" v-if="this.isAscendingPerson === false">mdi-chevron-down</v-icon>
          <v-icon left small class="ml-1" v-if="this.isAscendingPerson === true">mdi-chevron-up</v-icon>
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
      isAscendingTitle: null,
      isAscendingPerson: null,
      projects: [
        {title: 'Design front page', person: '1', due: '01/01/2020', status: 'complete'},
        {title: 'Design backend', person: '3', due: '16/02/2020', status: 'overdue'},
        {title: 'Publish video thumbinals', person: '6', due: '12/03/2020', status: 'ongoing'},
        {title: 'Create forum', person: '9', due: '01/03/2020', status: 'ongoing'},
      ]
    }
  },
  methods: {
    sortBy(prop) {
      if(prop === 'title') {
        if(!this.isAscendingTitle) {
        this.projects.sort((a, b) => {
            return a[prop] < b[prop] ? -1 : 1
          })
          this.isAscendingTitle = true
          this.isAscendingPerson = null
          
        } else {
          this.projects.sort((a, b) => {
            return a[prop] < b[prop] ? 1 : -1
          })
          this.isAscendingTitle = false
          this.isAscendingPerson = null
        }
      } else if(prop === 'person') {
        if(!this.isAscendingPerson) {
        this.projects.sort((a, b) => {
            return a[prop] < b[prop] ? -1 : 1
          })
          this.isAscendingPerson = true
          this.isAscendingTitle = null
          
        } else {
          this.projects.sort((a, b) => {
            return a[prop] < b[prop] ? 1 : -1
          })
          this.isAscendingPerson = false
          this.isAscendingTitle = null
        }
      }
    },
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
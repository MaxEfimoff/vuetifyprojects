<template>
  <div class="projects">
    <h1 class="subheading grey--text">projects</h1>

    <v-container class="my-5">
      <v-expansion-panels>
        <v-expansion-panel v-for="project in myProjects" :key="project.title">
        <v-expansion-panel-header>{{project.title}}</v-expansion-panel-header>
          <v-expansion-panel-content class="grey--text">
            <div class="font-weight-bold">{{project.due}}</div>
            <div>{{project.content}}</div>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-container>

  </div>
</template>

<script>

export default {
  computed: {
    myProjects() {
      return this.projects.filter(project => project.person === 'Max Efi')
    }
  },
  data() {
    return {
      projects: [
        {title: 'Design front page', person: 'Max Efi', due: '01/01/2020', status: 'complete', content: 'lorem fbd sgth sgfh sgh sfgh  styhat atharh atyhah ath hathar'},
        {title: 'Design backend', person: 'John Doe', due: '16/02/2020', status: 'overdue', content: 'lorem fbd sgth sgfh sgh sfgh  styhat atharh atyhah ath hathar'},
        {title: 'Publish video thumbinals', person: 'Will Smith', due: '12/03/2020', status: 'ongoing', content: 'lorem fbd sgth sgfh sgh sfgh  styhat atharh atyhah ath hathar'},
        {title: 'Create forum', person: 'Adam Yates', due: '01/03/2020', status: 'ongoing', content: 'lorem fbd sgth sgfh sgh sfgh  styhat atharh atyhah ath hathar'},
      ]
    }
  }
};
</script>

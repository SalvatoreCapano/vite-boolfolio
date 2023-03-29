<script>

import axios from 'axios';

import ProjectCard from './components/ProjectCard.vue'

export default {
  name: "App",
  components: {
    ProjectCard
  },
  data() {
    return {
      host: 'http://127.0.0.1:8000',
      data: null,
    }
  },
  methods: {
    getProjects() {
      // console.log('Richiesta progetti...')
      axios.get(`${this.host}/api/projects`)
        .then((response) => {
          console.log ('Dati risposta:', response.data);
          this.data = response.data.projects;
        });
      // console.log('Risposta ottenuta.')
    }
  },
  created() {
    this.getProjects();
  }
};
</script>


<template>
  <div class="container">
    <h1>Projects</h1>
    <div class="cardsContainer" v-if="this.data != null">
      <ProjectCard v-for="elem in this.data" :project="elem"/>
    </div>
    <p v-else>Caricamento Progetti...</p>
  </div>
</template>

<style lang="scss">
@use './style/main.scss' as *;

.container {
  max-width: 1360px;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.cardsContainer {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

p {
  color: white;
}
</style>
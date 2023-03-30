<script>

import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue'

export default {
  name: 'AppProjects',
  components: {
    ProjectCard
  },
  data() {
    return {
      host: 'http://127.0.0.1:8000',
      data: null,
      page: 1,
      lastPage: 1
    }
  },
  methods: {
    getProjects() {
      // console.log('Richiesta progetti...');
      axios.get(`${this.host}/api/projects`, {
        params: {
          page: this.page
        }
      })
        .then((response) => {
          console.log('Dati risposta:', response.data);
          this.data = response.data.projects; //Senza paginazione
          this.data = response.data.projects.data; //Con paginazione
          this.lastPage = response.data.projects.last_page;
        });
      // console.log('Risposta ottenuta.')
    },
    setPage(direction) {

      if (direction == 'prev' && this.page > 1) {
        this.page--;
        this.getProjects();
      }
      else if (direction == 'next' && this.page < this.lastPage) {
        this.page++;
        this.getProjects();
      }

    }
  },
  created() {
    this.getProjects();
  }
}
</script>

<template>
  <div class="cardsContainer" v-if="this.data != null">
    <ProjectCard v-for="elem in this.data" :project="elem" />
  </div>

  <p v-else>Caricamento Progetti...</p>

  <div class="controls">

    <button @click="this.setPage('prev')">
      <i class="bi bi-chevron-left"></i>
    </button>

    <span>Page {{ this.page }}</span>

    <button @click="this.setPage('next')">
      <i class="bi bi-chevron-right"></i>
    </button>

  </div>
</template>

<style lang="scss" scoped>
.cardsContainer {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;

  margin-bottom: 2rem;
}

p {
  text-align: center;
  color: white;
  margin-bottom: 1.25rem;
}

.controls {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;

  span {
    color: white;
  }
}
</style>
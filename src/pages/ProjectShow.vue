<script>

import axios from 'axios';

export default {
  name: 'ProjectShow',
  props: {
    project: Object
  },
  data () {
    return {
      host: 'http://127.0.0.1:8000',
      project: null
    }
  },
  created() {
    this.getProject();
  },
  methods: {
    getProject() {
      axios
        .get(`${this.host}/api/projects/${this.$route.params.slug}`)
        .then(response => {
          console.log(response.data);
          if (response.data.success) {
            this.project = response.data.project;
          }
          else {
            // this.$router.push({ name: 'not-found' });
            console.log ("Non trovato")
          }
        });
    }
  }
}
</script>

<template>
  <div class="card" v-if="this.project">
    <h3 class="cardId">#{{ this.project.id }}</h3>
    <div class="imgContainer">
      <img :src="this.project.full_image_path" alt="">
    </div>
    <h2 class="cardTitle">{{ this.project.title }}</h2>
    <!-- <p class="cardDescription">{{ this.project.description }}</p> -->
    <span class="cardStatus">Status: {{ this.project.status }}</span>
  </div>
</template>

<style lang="scss" scoped>
.card {
  width: 500px;
  height: 400px;
  padding: 10px;
  border-radius: 16px;
  border: 2px solid #444444;
  background-color: #343434;
  cursor: pointer;

  .cardId {
    color: white;
    margin-bottom: 5px;
  }

  .imgContainer {
    width: 100%;

    img {
      width: 100%;
    }
  }

  .cardTitle {
    font-size: 1rem;
    color: white;
    margin-bottom: 5px;
  }

  .cardStatus {
    color: white;
  }

  &:hover {
    background-color: #404040;
  }

  button {
    text-transform: capitalize;
    padding: 2px 4px;
  }
}
</style>
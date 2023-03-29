<script>

  import axios from 'axios';

  // import HelloWorld from './components/HelloWorld.vue'

  export default {
  name: "App",
  components: {
  },
  data () {
    return {
      host: 'http://127.0.0.1:8000'
    }
  },
  methods: {
    getProjects() {
      console.log('Richiesta progetti...')
      axios.get(`${this.host}/api/projects`)
      .then ((response) => {
        console.log ('Dati risposta:', response.data);
      });
      console.log('Risposta ottenuta.')
    }
  },
  created () {
    this.getProjects();
  }
};
</script>


<template>
  <div class="container">
    
  </div>
</template>

<style>
  .container {
    /* display: flex;
    justify-content: center;
    align-items: center; */
    max-width: 1360px;
    margin: 0 auto;
  }
</style>
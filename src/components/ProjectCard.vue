<script>

export default {
  name: 'ProjectCard',
  props: {
    project: Object
  }
}
</script>

<template>
  <div class="card">
    <h3 class="cardId">#{{ this.project.id }}</h3>
    <h2 class="cardTitle">{{ this.project.title }}</h2>
    <!-- <p class="cardDescription">{{ this.project.description }}</p> -->
    <span class="cardStatus">Status: {{ this.project.status }}</span>
  </div>
</template>

<style lang="scss" scoped>
  .card {
    width: 200px;
    height: 200px;
    padding: 10px;
    border-radius: 16px;
    border: 2px solid #444444;
    background-color: #343434;
    cursor: pointer;
    
    .cardId {
      color: white;
      margin-bottom: 5px;
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
  }
</style>
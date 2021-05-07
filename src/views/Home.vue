<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
          <p>{{project.title}}</p>
      </div>

    </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  components: {

  },
  data(){
      return {
        projects: []
      }
    },

    async mounted(){
      try{
        const resp = await fetch('http://localhost:3000/projects');
        const data = await resp.json();
        console.log(data);
        return this.projects = data;
      }catch(err){
        console.log('Error: ', err)
      }
    }
    
}
</script>

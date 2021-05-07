<template>
  <div class="home">
    <div v-if="projects.length">
      <div v-for="project in projects" :key="project.id">
          <SingleProject 
            :project= "project"
          />
      </div>

    </div>
  </div>
</template>

<script>
import SingleProject from '../components/SingleProject';

export default {
  name: 'Home',
  components: {
    SingleProject
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

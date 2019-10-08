<template>
  <ul >

    <li v-for="dador of dadores" :key="dador.codigo">
      <p><strong>{{dador.nome}}</strong></p>
     
    </li>
<ul v-if="errors && errors.length">
    <li v-for ="error of errors" :key="error">
      {{error.message}}
    </li>
  </ul>
    
  </ul>
</template>
<script>
import axios from 'axios';

export default {
  data() {
    return {
      dadores: [],
      errors: []
    }
  },

  // Fetches posts when the component is created.
  mounted() {
    axios.get(`https://sanguemozapi.herokuapp.com/api/dadores`)
    .then(response => {
      // JSON responses are automatically parsed.
      this.dadores = response.data
      console.log(dadores)
      console.log("--------------")
      console.log(dadores)
    })
    .catch(e => {
      this.errors.push(e)
    })

    // async / await version (created() becomes async created())
    //
    // try {
    //   const response = await axios.get(`http://jsonplaceholder.typicode.com/posts`)
    //   this.posts = response.data
    // } catch (e) {
    //   this.errors.push(e)
    // }
  }
}
</script>
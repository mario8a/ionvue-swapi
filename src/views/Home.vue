<template>
  <div>
    <ion-card v-for="post in posts" :key="post.episode_id">
      <ion-card-header>
        <h3>{{post.title}}</h3>
      </ion-card-header>
        <ion-card-content>
          {{post.opening_crawl}}
         </ion-card-content>
          <ion-item>
            <ion-icon name="walk" slot="start"></ion-icon>
            <ion-label>Director: {{post.director}}</ion-label>
        </ion-item>
    </ion-card>
  </div>
</template>


<script>
import axios from 'axios';

export default {
  data() {
    return {
       posts: [],
       //results: []
    }
  },
  async mounted() {
    await axios.get(`https://swapi.co/api/films`)
            .then(resp => {
              this.posts = resp.data.results
              // console.log(this.posts);
              // this.posts.forEach(function(data){
              //   // console.log(data);
              // })
            })    
  },
  methods: {

  }
}
</script>
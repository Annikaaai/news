<template>
  <v-app>
    <v-container>
      <v-row>

           <v-col ><!-- v-for="(item, i) in news" v-bind:key="i" -->
            <v-card>
              <v-img>
                <v-card-title></v-card-title>
              </v-img>

              <v-card-text>
                <p>
                  Lorem ipsum, dolor sit amet consectetur adipisicing elit. Odio dolorum illum accusamus eos nam atque placeat incidunt, repellendus facere tempora ratione omnis eius minus, quis autem beatae! Quis, reprehenderit aliquid distinctio corporis molestias excepturi! Maxime, nobis numquam. Similique, reiciendis tenetur voluptate sunt voluptatem assumenda eius asperiores, ipsum, eligendi sint perferendis.
                </p>
              </v-card-text>
            </v-card>
          </v-col>

      </v-row>
    </v-container>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    news: []
  }),
  methods: () => ({
    // getNews() {
    //   this.axios.get('https://newsapi.org/v2/top-headlines?country=ru&apiKey=d7f41a32c26b4bbfb596d58b1a54c766&roistat_visit=3523472')       
    //   .then((response) => {    
    //     this.news = response.data.articles;
    //     console.log(this.news[0])
    //   })   
    // },

    // getNews() {
    //   this.axios.get('https://newsapi.org/v2/top-headlines?country=ru&apiKey=d7f41a32c26b4bbfb596d58b1a54c766&roistat_visit=3523472')       
    //   .then((response) => {    
    //     console.log(1)     
        
    //     this.news = response.data.articles
    //     console.log(this.news[0].title) 
    //   })   
    // },


    getNews(){
      this.axios({
      method: "GET",
      url: 'https://newsapi.org/v2/top-headlines?country=us8apiKey-d7f41a32c26b4bbfb596d58b1a54c766',
      }).then( (response) =>{
        this.news = response.data.articles;
      })
    }
    
  }),
  mounted(){
    this.getNews();
  }
};
</script>
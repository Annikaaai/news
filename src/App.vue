<template>
  <v-app>
    <v-container>
      <v-row>

           <v-col cols = "12" sm = "4" v-for="(item, i) in news" v-bind:key="i">
            <v-card>
              <v-img
              v-bind:src = "item.urlToImage"
              >
                
              </v-img>
              <v-card-title v-text = "item.title"></v-card-title>
              <v-card-text>
                <p>
                  {{ item.content }}
                </p>
              </v-card-text>

              <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn plain color="deep-purple" v-bind:href="item.url">
                <v-icon class="mr-2">mdi-link-variant</v-icon> Читать в источнике
            </v-btn>
            </v-card-actions>
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
  methods: {
    getNews() {
      this.axios.get('https://newsapi.org/v2/top-headlines?country=us&apiKey=d7f41a32c26b4bbfb596d58b1a54c766')       
      .then((response) => {    
        this.news = response.data.articles;
        console.log(this.news)
      })   
    },
// https://newsapi.org/v2/top-headlines?country=ru&apiKey=d7f41a32c26b4bbfb596d58b1a54c766&roistat_visit=3523472
    // getNews() {
    //   this.axios.get('https://newsapi.org/v2/top-headlines?country=ru&apiKey=d7f41a32c26b4bbfb596d58b1a54c766&roistat_visit=3523472')       
    //   .then((response) => {    
    //     console.log(1)     
        
    //     this.news = response.data.articles
    //     console.log(this.news[0].title) 
    //   })   
    // },


    // getNews(){
    //   this.axios({
    //   method: "GET",
    //   url: 'https://newsapi.org/v2/top-headlines?country=us8apiKey-d7f41a32c26b4bbfb596d58b1a54c766',
    //   }).then( (response) =>{
    //     this.news = response.data.articles;
    //   })
    // }
    
  },
  mounted(){
    this.getNews();
  }
};
</script>
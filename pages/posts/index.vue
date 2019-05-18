<template>
    <v-app>
       <v-layout>
          <v-flex xs12>
             <h1 class="display-2"> Posts Pages </h1>
          </v-flex>
       </v-layout>
       <v-layout row-wrap>
          <v-flex xs12 m6 l3 v-for="post in posts" :key="post.id">
             <v-card color="success" dark>
                <v-card-title>
                   <v-icon>description</v-icon>
                   <span class="title font-weight-light"> {{ post.title }} </span>
                </v-card-title>
                <v-card-text class="headline font-weight-bold">
                   {{ post.body }}
                </v-card-text>
                <v-card-actions>
                   <v-spacer/>
                   <nuxt-link :to="{name: 'posts-id', params: {id: post.id}}">
                      <v-btn flat> See more </v-btn>
                   </nuxt-link>
                </v-card-actions>
             </v-card>
          </v-flex>
       </v-layout>
    </v-app>
</template>

<script>
   import axios from 'axios'

    export default {
       name: "index",
       async asyncData () {
          let response = await axios.get('https://jsonplaceholder.typicode.com/posts');
          return {
             posts: response.data
          }
       }
    }
</script>

<style scoped>

</style>

<template>
    <v-container>
       <h1 class="display-2"> Post #{{ post.id }} </h1>

       <v-layout row-wrap>
         <v-flex sm9>
            <v-card color="blue-red" class="white--text">
               <v-card-title>
                  {{ post.title }}
               </v-card-title>
               {{ post.body }}
            </v-card>
         </v-flex>
          <v-flex sm3>
             <v-btn color="secondary" outline
             v-for="other in others" :key="other.id">
                <nuxt-link :to="{name: 'posts-id', params: {id: other.id}}">
                   {{ other.title }}
                </nuxt-link>
             </v-btn>
          </v-flex>
       </v-layout>
    </v-container>
</template>

<script>
   import axios from 'axios'

    export default {
       name: "_id.vue",
       data() {
          return {
             id: this.$route.params.id
          }
       },
       async asyncData (context) {
          let response = await axios.get(`https://jsonplaceholder.typicode.com/posts/${context.params.id}`);
          return {post: response.data}
       }
    }
</script>

<style scoped>
   a {
      color: orangered;
   }
</style>

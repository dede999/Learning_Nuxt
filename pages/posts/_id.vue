<template>
    <v-container>
       <h1 class="display-1"> Post #{{ post.id }} </h1>

       <v-layout row-wrap>
         <v-flex s12>
            <v-card color="blue-red" class="white--text">
               <v-card-title>
                  {{ post.title }}
               </v-card-title>
               {{ post.description }}
            </v-card>
         </v-flex>
       </v-layout>
    </v-container>
</template>

<script>
    import post from "./post";

    export default {
       name: "_id.vue",
       data() {
          return {
             id: this.$route.params.id,
             posts: [
                {id: 1, title: "Feeding Rex", description: "Learn how to feed your dog"},
                {id: 2, title: "Breeding Rex", description: "Learn how to help your pal finding his/her soul mate"},
                {id: 3, title: "Adopting", description: "Where should I adopt my dog"}
             ]
          }
       },
       computed: {
          post () {
             return this.posts.find(post => post.id === this.id)
          }
       }
    }
</script>

<style scoped>

</style>

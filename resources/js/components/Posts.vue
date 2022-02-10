<template>
   <div class="container">
      <h3>Ecco la lista dei Post</h3>

      <SinglePost 
         v-for="post in posts"
         :key="post.id"
         :post="post"
      />
   </div>
</template>

<script>

import SinglePost from './partials/SinglePost.vue'

export default {
   name: "Posts",
   components:{
      SinglePost
   },
   data(){
      return{
         urlApi: 'http://127.0.0.1:8000/api/posts',
         posts: null
      }
   },
   mounted(){
      this.printPosts();
   },
   methods:{
      printPosts(){
         axios.get(this.urlApi)
         .then(result => {
            this.posts = result.data.posts
            // console.log(result.data.posts);
         })
      }
   }
}
</script>

<style lang="scss" scoped>
h3{
   padding: 35px 0;
}

.container{
   width: 65%;
   margin: 0 auto;
}
</style>
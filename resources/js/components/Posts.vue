<template>
   <div class="container">
      <h3>Ecco la lista dei Post</h3>

      <SinglePost 
         v-for="post in posts"
         :key="post.id"
         :post="post"
      />

      <button
      @click="printPosts(pages.current - 1)"
      >Prev Page</button>

      <button
      @click="printPosts(pages.current + 1)"
      >Next Page</button>

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
         urlApi: 'http://127.0.0.1:8000/api/posts?page=',
         posts: null,
         pages: {}
      }
   },
   mounted(){
      this.printPosts();
   },
   methods:{
      printPosts(page = 1){
         axios.get(this.urlApi + page)
         .then(result => {
            this.posts = result.data.posts.data
            // console.log(result.data.posts);
            this.pages = {
               current : result.data.posts.current_page,
               last : result.data.posts.last_page
            }
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
   button{
      margin: 20px 0;
   }
}
</style>
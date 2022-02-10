<template>
   <article>
      <h4><strong>{{ post.title_post }}</strong></h4>
      <p class="data">{{ post.created_at }}</p>
      <p class="content">{{ post.content }}</p>
   </article>
</template>

<script>
export default {
   name: "SinglePost",
   props:{
      'post': Object
   }
}
</script>

<style lang="scss" scoped>
h4{
   margin: 25px 0 5px;
}
.data{
   font-size: 12px;
   font-style: italic;
   margin-bottom: 15px;
}
</style>
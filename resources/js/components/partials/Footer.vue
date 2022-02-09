<template>
   <footer>

      <h5>Un magnifico Footer</h5>

   </footer>
</template>

<script>
export default {
   name: "Footer"
}
</script>

<style lang="scss" scoped>

footer{
   height: 50px;
   width: 100vw;
   line-height: 50px;
   position: fixed;
   bottom: 0;
   background-color: gray;
   display: flex;
   justify-content: center;
   align-self: center;
}

</style>
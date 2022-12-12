<template>
  <panel title="recentlyViewed">

    <img width = "440 px" v-for = "img in images" v-bind:src="img"/>
    
  </panel>
</template>

<script>
export default {
  data () {
    return {
      images: ['http://34.85.205.24:5000//getRecent?user_id=ritik.jain@gmail.com']
    }
  }
}

</script>

<style scoped>
</style>

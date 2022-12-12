import {myVariable} from '@/components/Songs/SongsSearchPanel'

<template>
 <panel title="Image Generated">
   <p>Message is: {{myVariable}}</p>
    <img width = "440 px" v-for = "img in images" v-bind:src="img"/>
    
  </panel>
  
</template>


<script>
export default {
  data () {
    return {
      images: ['http://34.85.205.24:5000//store?user_id=ritik.jain@gmail.com&caption='A man riding a horse on moon']
    }
  }
}
</script>


<style scoped>
</style>

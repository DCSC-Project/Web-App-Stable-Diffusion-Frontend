<template>
  <panel title="Image Generated">

    <img v-for="image in images" :key="image" :src="image" />
    
    
  </panel>
  
</template>

<script>
import axios from 'axios'
import JSZip from 'jszip'

export default {
  data () {
    return {
      images: ['https://imageio.forbes.com/specials-images/imageserve/5d35eacaf1176b0008974b54/0x0.jpg?format=jpg&crop=4560,2565,x790,y784,safe&width=1200']
    }
  },
  mounted () {
    this.demo()
  },
  methods: {
    async demo () {
      console.log('here')
      let tempImages = []
      axios.get('http://34.85.205.24:5000//getRecent?user_id=ritik.jain@gmail.com', {responseType: 'blob'})
      .then(function (response) {
        console.log(response)
        const zip = new JSZip()
        zip.loadAsync(response.data, {blob: true}).then(function (zip) {
          console.log(tempImages)
        })
      })
      await new Promise(resolve => setTimeout(resolve, 10000))
      for (let i = 0; i < tempImages.length; i++) {
        this.images.push(tempImages[i])
      }
    }
  }
}

</script>


<style scoped>
</style>

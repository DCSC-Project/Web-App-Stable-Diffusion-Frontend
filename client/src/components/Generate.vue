<template>
  <panel title="Image Generated">

    <img v-for="image in images" :key="image" :src="image" />
    
    
  </panel>
  
</template>

<script>
import axios from 'axios'
import JSZip from 'jszip'
import { saveAs } from 'file-saver'

export default {
  data () {
    return {
      images: ['https://i.ibb.co/kBLmBHk/0000020221211-225126.png']
    }
  },
  mounted () {
    this.demo()
  },
  methods: {
    async demo () {
      let tempImages = []
      try {
        axios.get("http://34.85.205.24:5000//store?user_id=akhil.test@gmail.com&caption='A man riding a horse on moon'", {responseType: 'blob'}).then(function (response) {
          console.log(response)
          const zip = new JSZip()
          zip.loadAsync(response.data, {blob: true}).then(function (zip) {
            const files = Object.keys(zip.files)
            console.log(typeof files)
            var bytes = new Uint8Array(files.length)
            for (var i = 0; i < files.length; i++) {
              bytes[i] = files.charCodeAt(i)
            }
            var blob = new Blob([bytes], {type: 'application/zip'})
            saveAs(blob, 'download.zip')
            for (let i = 0; i < files.length; i++) {
              tempImages.push(files[i])
            }
            console.log(tempImages)
          })
        })
        for (let i = 0; i < tempImages.length; i++) {
          this.images.push(tempImages[i])
          console.log(typeof this.image[i])
        }
      } catch (error) {
        console.log(error)
      }
    }
  }
}

</script>


<style scoped>
</style>

<template>
  <v-layout>
    

    <v-flex :class="{
        xs12: isUserLoggedIn
      }" class="ml-2">
      <songs-search-panel />
    </v-flex>
    
  </v-layout>
</template>

<script>
import SongsSearchPanel from './SongsSearchPanel'
import {mapState} from 'vuex'

export default {
  components: {
    SongsSearchPanel
  },
  computed: {
    ...mapState([
      'isUserLoggedIn'
    ])
  },
  data () {
    return {
      songs: null
    }
  }
}
</script>


<style scoped>
.song {
  padding: 20px;
  height: 330px;
  overflow: hidden;
}

.song-title {
  font-size: 30px;
}

.song-artist {
  font-size: 24px;
}

.song-genre {
  font-size: 18px;
}

.album-image {
  width: 70%;
  margin: 0 auto;
}
</style>


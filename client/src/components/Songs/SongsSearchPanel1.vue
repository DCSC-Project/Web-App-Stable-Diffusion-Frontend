<template>
  <panel title="Generate" >
    <v-text-field
      label="Input text to generate image"
      v-model="search"
    ></v-text-field>
     <v-btn
            dark
            class="cyan" @click="generate">
            Generate
          </v-btn>
  </panel>
  
</template>

<script>
import _ from 'lodash'

export default {
  methods: {
    generate () {
      this.$router.push({
        name: 'generate'})
    }
  },
  data () {
    return {
      search: ''
    }
  },
  watch: {
    search: _.debounce(async function (value) {
      const route = {
        name: 'songs'
      }
      if (this.search !== '') {
        route.query = {
          search: this.search
        }
      }
      this.$router.push(route)
    }, 700),
    '$route.query.search': {
      immediate: true,
      handler (value) {
        this.search = value
      }
    }
  }
}
</script>

<style>

</style>







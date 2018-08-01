<template>
  <v-layout>
    <v-flex text-xs-center>
      <a href="https://www.reddit.com/api/v1/authorize?client_id=6j6q8xJMzLZDYQ&response_type=code&state=signup&redirect_uri=http://localhost:3000/signup/&duration=temporary&scope=mysubreddits identity">Sign up</a>
      window.location.search
    </v-flex>
  </v-layout>
</template>
<script>
  import axios from 'axios'
  function parseSearchString (searchString) {
    let parsed = {}
    if (searchString.charAt(0) === '?') searchString = searchString.substring(1)
    searchString.split('&').forEach(query => {
      let [key, value] = query.split('=')
      parsed[key] = value
    })
    return parsed
  }
  export default {
    data () {
      return {
        adsf: 'asdf'
      }
    },
    mounted () {
      if (window && window.location && window.location.search) {
        let searchObject = parseSearchString(window.location.search)
        if (searchObject.error) alert(searchObject.error)
        else axios.post('http://localhost:3412', searchObject).then(console.log).catch(console.log)
      } else alert('no search string found')
    }
  }
</script>

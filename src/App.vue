<template>
    <the-header title="Learning Resources"></the-header>
        <stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue'  
import StoredResources from './components/learning-resources/StoredResources.vue'

export default {
  data() {
    return {
      storedResources: [
        {
          id: 'official-guide',
          title: 'Official guide',
          description: 'Vue JS docs.',
          link: 'https://vuejs.org'
        },
        {
          id: 'google-guide',
          title: 'Google guide',
          description: 'Learn to google.',
          link: 'https://google.com'
        },
      ]
    }
  },
  components: { StoredResources, TheHeader },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>

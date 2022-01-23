<template>
<div class="bg-white sm:bg-gray-900 h-screen w-full">
    <div class="container">
        <Header :text="title" />

        <Home @update="updates"/>
    </div>
</div>
</template>

<script>
import Header from './components/Header'
import Home from './views/Home'

export default {
  name: 'App',
  data() {
    return {
      title: 'Global'
    }
  },
  components: {
    Header,
    Home
  },
  methods: {
    updates(country) {
      this.title = country.Country
    }
  }
}
</script>



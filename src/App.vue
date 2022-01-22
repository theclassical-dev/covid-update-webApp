<template>
    <div class="container">
        <Header />

        <Home />
    </div>

</template>

<script>
import Header from './components/Header'
import Home from './views/Home'

export default {
  name: 'App',
  components: {
    Header,
    Home
  }
}
</script>



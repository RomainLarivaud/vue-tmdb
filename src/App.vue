<template>
    <div id="app">
        <Header/>
        <MostPopular/>
        <NowPlaying/>
        <LastUpcoming/>
        <Footer/>
    </div>
</template>

<script>
import Header from './components/Header.vue'
import MostPopular from './components/MostPopular.vue'
import NowPlaying from './components/NowPlaying.vue'
import LastUpcoming from './components/LastUpcoming.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    MostPopular,
    NowPlaying,
    LastUpcoming,
    Footer
  }
}
</script>
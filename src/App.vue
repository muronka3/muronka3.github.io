<template>
  <div id="app">
    <HeaderBlock />
    <main>
      <SectionHero />
      <SectionAbout />
      <SectionPortfolio />
      <SectionReviews />
    </main>
  </div>
</template>

<script>
import HeaderBlock from './components/HeaderBlock.vue';
import SectionHero from './components/SectionHero.vue';
import SectionAbout from './components/SectionAbout.vue';
import SectionPortfolio from './components/SectionPortfolio.vue';
import SectionReviews from './components/SectionReviews.vue';

export default {
  name: 'App',
  components: {
    HeaderBlock,
    SectionHero,
    SectionAbout,
    SectionPortfolio,
    SectionReviews
  }
}
</script>

<style scoped>
#app {
  font-family: 'Sono', monospace, sans-serif;
  background: var(--color-bg, #FDFDFD);
  color: var(--color-text, #313131);
  min-height: 100vh;
}
main {
  width: 100%;
  overflow-x: hidden;
}
</style>

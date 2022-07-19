<template>
  <div class="home">
    <Header />
    <main>
      <Hero />
    </main>
  </div>
</template>

<script>
import Header from '@/components/HomeView/Header/Header';
import Hero from "@/components/HomeView/Hero/Hero";

export default {
  name: 'HomeView',
  components: {
    Header, Hero
  }
}
</script>
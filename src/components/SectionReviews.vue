<template>
  <section id="reviews" class="reviews-section">
    <ParallaxBackground />
    <div class="reviews-carousel">
      <Carousel :itemsToShow="1.2" :wrapAround="false" :mouseDrag="true" :snapAlign="'start'" :scrollPerPage="false" class="carousel">
        <Slide v-for="n in 5" :key="n">
          <ReviewCard />
        </Slide>
      </Carousel>
    </div>
    <div class="reviews-contact">
      <h2>Contact Me</h2>
      <div class="contact-links">
        <a href="#" class="contact-link">Email</a>
        <a href="#" class="contact-link">WhatsApp</a>
        <a href="#" class="contact-link">Telegram</a>
        <a href="#" class="contact-link">Instagram</a>
      </div>
    </div>
    <div class="reviews-character">
      <AnimatedCharacter type="follow-cursor" />
    </div>
  </section>
</template>

<script>
import ParallaxBackground from './ParallaxBackground.vue';
import AnimatedCharacter from './AnimatedCharacter.vue';
import ReviewCard from './ReviewCard.vue';
import { Carousel, Slide } from 'vue3-carousel';
import 'vue3-carousel/dist/carousel.css';

export default {
  name: 'SectionReviews',
  components: { ParallaxBackground, AnimatedCharacter, ReviewCard, Carousel, Slide },
};
</script>

<style scoped>
.reviews-section {
  min-height: 100vh;
  background: #F4F4F4;
  position: relative;
  padding: var(--spacing-lg) 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}
.reviews-carousel {
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: var(--spacing-md);
  margin-bottom: var(--spacing-lg);
  position: relative;
  z-index: 2;
}
.carousel {
  width: 90vw;
  max-width: 1400px;
}
.reviews-contact {
  width: 100vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: var(--spacing-md);
  z-index: 2;
}
.reviews-contact h2 {
  font-size: 2.5rem;
  margin: 0;
}
.contact-links {
  display: flex;
  gap: 36px;
  flex-wrap: wrap;
  justify-content: center;
}
.contact-link {
  font-size: 1.5rem;
  color: var(--color-text);
  text-decoration: none;
  padding: 10px 24px;
  border-radius: 9999px;
  transition: background 0.2s, color 0.2s;
}
.contact-link:hover {
  background: var(--color-accent);
}
.reviews-character {
  position: absolute;
  bottom: 40px;
  right: 10vw;
  z-index: 3;
}
</style> 
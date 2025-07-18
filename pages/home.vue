<script setup>
import { ref, onMounted } from "vue";
definePageMeta({
  title: "Home",
  layout: "home",
});

const heroTextItem = ref(null);

onMounted(() => {
  setTimeout(() => {
    heroTextItem.value.style.opacity = "1";
    heroTextItem.value.style.transform = "translateY(0)";
  }, 300);
});
</script>

<template>
  <div class="hero">
    <div class="blur-bg"></div>
    <img src="@/assets/images/homeimg.jpeg" alt="Hero Image" class="hero-img" />
    <div class="hero-text" ref="heroTextItem">
      <h1>NEW DROP ONLINE NOW</h1>
      <a href="products" class="shop-btn-link">
        <button class="shop-btn">Shop Now</button>
      </a>
    </div>
  </div>
</template>

<style scoped>
.hero {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
}

.blur-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image: url("@/assets/images/homeimg.jpeg");
  background-size: cover;
  background-position: bottom;
  filter: blur(25px);
  transform: scale(1.1);
  z-index: 0;
}

.hero-img {
  position: relative;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: left 15%;
  z-index: 1;
}

.hero-text {
  position: absolute;
  bottom: 40px;
  left: 40px;
  color: white;
  z-index: 2;
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.9s ease-in-out;
}

.hero-text h1 {
  font-size: 28px;
  margin-bottom: 15px;
}

.shop-btn {
  padding: 12px 24px;
  background-color: white;
  color: black;
  border: none;
  font-size: 16px;
  text-transform: uppercase;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
}

.shop-btn:hover {
  background-color: black;
  color: white;
}
</style>

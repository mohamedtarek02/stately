<script setup lang="ts">
import { ref, onMounted } from "vue";

const showNavbar = ref(false);

onMounted(() => {
  setTimeout(() => {
    showNavbar.value = true;
  }, 300);
});
</script>

<template>
  <nav :class="['navbar', showNavbar ? 'show' : '']">
    <ul class="nav-left">
      <li><NuxtLink to="/">Home</NuxtLink></li>
      <li><NuxtLink to="/catalog">Catalog</NuxtLink></li>
      <li><NuxtLink to="/contact">Contact</NuxtLink></li>
    </ul>
    <div class="logo">STↃTELY</div>
    <ul class="nav-right">
      <li class="flex gap-1 items-end">
        <FontAwesomeIcon icon="fas fa-magnifying-glass" class="w-4 h-4" />
        <a href="#"><span class="material-symbols-outlined">search</span></a>
      </li>
      <li>
        <a href="#"><span class="material-symbols-outlined">person</span></a>
      </li>
      <li>
        <a href="#"
          ><span class="material-symbols-outlined">shopping_bag</span></a
        >
      </li>
    </ul>
  </nav>
</template>

<style scoped>
@font-face {
  font-family: "Brother Signature";
  src: url("assets/fonts/BrotherSignature-7BWnK.otf") format("opentype");
  font-weight: normal;
  font-style: normal;
}

.navbar {
  opacity: 0;
  transform: translateY(-20px);
  transition: all 0.8s ease;
  position: absolute;
  top: 0;
  width: 100%;
  padding: 1px 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: white;
  z-index: 2;
}

.navbar.show {
  opacity: 1;
  transform: translateY(0);
}

.navbar ul {
  list-style: none;
  display: flex;
  gap: 20px;
  padding: 0;
  margin: 0;
}

.navbar a {
  text-decoration: none;
  color: white;
  font-weight: 500;
  font-size: 12px;
  font-style: italic;
  transition: color 0.3s ease;
}

.navbar a:hover {
  color: black;
}

.logo {
  font-family: "Brother Signature", cursive;
  font-size: 24px;
}
</style>

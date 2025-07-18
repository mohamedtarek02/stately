<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";

const showNavbar = ref(false);
const menuOpen = ref(false);
const router = useRouter();

onMounted(() => {
  setTimeout(() => {
    showNavbar.value = true;
  }, 300);
});

function toggleMenu() {
  menuOpen.value = !menuOpen.value;
}
</script>

<template>
  <div class="pages-content">
    <slot></slot>

    <nav :class="['navbar', showNavbar ? 'show' : '']">
      <ul class="nav-right">
        <li class="flex gap-1 items-end">
          <FontAwesomeIcon icon="fas fa-cart-shopping" class="w-9 h-7" />
        </li>
        <li class="flex gap-1 items-end">
          <FontAwesomeIcon icon="fas fa-user" class="w-9 h-7" />
        </li>
      </ul>

      <div class="logo">Stately</div>

      
      <div class="menu-icon" @click="toggleMenu">
        <FontAwesomeIcon icon="fas fa-bars" class="w-9 h-7" />
      </div>

      
      <div v-if="menuOpen" class="menu-drawer">
        <div class="close-area" @click="toggleMenu"></div>
        <div class="menu-content">
          <NuxtLink to="/" @click="toggleMenu">Home</NuxtLink>
          <NuxtLink to="/products" @click="toggleMenu">shop all</NuxtLink>
          <NuxtLink to="/contact" @click="toggleMenu">Contact us</NuxtLink>
          <NuxtLink to="/about us" @click="toggleMenu">about us</NuxtLink>
        </div>
      </div>
    </nav>
  </div>
</template>

<style lang="scss" scoped>
.pages-content {
  padding-top: 80px;
  min-height: 100vh;
  background-color: #fafafa;
  border-radius: 8px;
}

@font-face {
  font-family: "Brother Signature";
  src: url("@/assets/fonts/BrotherSignature-7BWnK.otf") format("opentype");
  font-weight: normal;
  font-style: normal;
}

.logo {
  font-family: "Brother Signature", cursive;
  font-size: 50px;
  color: black;
  letter-spacing: 18px;
}

.navbar {
  opacity: 0;
  transform: translateY(-20px);
  transition: all 0.8s ease;
  position:absolute;
  top: 0;
  width: 100%;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: black;
  z-index: 100;
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
  color: black;
  font-weight: 500;
  font-size: 12px;
  font-style: italic;
  transition: color 0.3s ease;
}

.navbar a:hover {
  color: black;
}

.icon,
.menu-icon,
.navbar .nav-right li {
  color: black;
  font-size: 25px;
  cursor: pointer;
}


.menu-drawer {
  position: fixed;
  top: 0;
  right: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  z-index: 999;
}

.close-area {
  flex: 1;
  background-color: rgba(0, 0, 0, 0.5);
}

.menu-content {
  width: 250px;
  background-color: white;
  padding: 40px 20px;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.menu-content a {
  color: black;
  font-size: 18px;
  font-weight: bold;
  text-decoration: none;
}

.menu-content a:hover {
  color: GREY;
}
</style>

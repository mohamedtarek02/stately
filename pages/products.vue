<script setup>
import { onMounted } from "vue";

definePageMeta({
  title: "Home",
  layout: "default",
});

onMounted(() => {
  const products = document.querySelectorAll(".product-card");

  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("show");
        }
      });
    },
    {
      threshold: 0.9,
    }
  );

  products.forEach((product) => observer.observe(product));
});
</script>

<template>
  <div class="products-grid">
    <div class="product-card">
      <a href="product1">
        <img
          src="assets/images/WhatsApp_Image_2025-06-29_at_10.06.23_PM-removebg-preview.png"
          alt="Product1"
        />
        <h3>White-Ivory</h3>
        <p>450.00 EG</p>
      </a>
    </div>
    <div class="product-card">
      <a href="product2.ht">
        <img
          src="/assets/images/WhatsApp_Image_2025-06-29_at_10.06.30_PM-removebg-preview.png"
          alt="Product 2"
        />
        <h3>Beige-Dune</h3>
        <p>450.00 EG</p>
      </a>
    </div>
    <div class="product-card">
      <a href="product3.html">
        <img
          src="assets/images/WhatsApp_Image_2025-06-29_at_10.06.34_PM-removebg-preview.png"
          alt="Product 3"
        />
        <h3>Grey-Ash</h3>
        <p>450.00 EG</p>
      </a>
    </div>
    <div class="product-card">
      <a href="product4.html">
        <img
          src="assets/images/WhatsApp_Image_2025-06-29_at_10.08.25_PM-removebg-preview.png"
          alt="Product 4"
        />
        <h3>Black-Raven</h3>
        <p>450.00 EG</p>
      </a>
    </div>
    <div class="product-card">
      <a href="product5.html">
        <img
          src="assets/images/WhatsApp_Image_2025-06-29_at_10.08.28_PM-removebg-preview.png"
          alt="Product 5"
        />
        <h3>black-noir</h3>
        <p>450.00 EG</p>
      </a>
    </div>
  </div>
</template>

<style>
.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 60px;
  padding: 100px 10px;
}

.product-card {
  opacity: 0;
  transform: translateY(40px);
  transition: all 0.8s ease-out;
}

.product-card.show {
  opacity: 1;
  transform: translateY(0);
}

.product-card:hover {
  transform: scale(1.3);
}

.product-card img {
  width: 100%;
  max-width: 300px;
  height: auto;
  object-fit: cover;
  border-radius: 18px;
}

.product-card h3 {
  margin: 10px 0 5px;
  font-size: 16px;
  color: #111;
  text-align:center;
}

.product-card p {
  font-weight: bold;
  color: #333;
}

a {
  text-decoration: none;
}
</style>

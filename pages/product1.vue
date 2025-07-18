<script setup>
import { onMounted } from "vue";

definePageMeta({
  title: "white-ivory",
  layout: "default",
});

onMounted(() => {
  const navbar = document.querySelector(".navbar");
  if (navbar) navbar.classList.add("show");

  const images = [
    "assets/images/WhatsApp_Image_2025-06-29_at_10.06.24_PM-removebg-preview.png",
    "assets/images/WhatsApp_Image_2025-06-29_at_10.06.34_PM-removebg-preview.png",
    "assets/images/WhatsApp_Image_2025-06-29_at_10.06.30_PM-removebg-preview.png",
    "assets/images/WhatsApp_Image_2025-06-29_at_10.08.25_PM-removebg-preview.png",
  ];

  let currentIndex = 0;
  const productImage = document.getElementById("product-image");
  const nextImageBtn = document.getElementById("next-image");
  const prevImageBtn = document.getElementById("prev-image");

  const updateImage = () => {
    if (productImage) {
      productImage.classList.remove("fade-in");
      void productImage.offsetWidth; // Force reflow
      productImage.src = images[currentIndex];
      productImage.classList.add("fade-in");
    }
  };

  nextImageBtn?.addEventListener("click", () => {
    currentIndex = (currentIndex + 1) % images.length;
    updateImage();
  });

  prevImageBtn?.addEventListener("click", () => {
    currentIndex = (currentIndex - 1 + images.length) % images.length;
    updateImage();
  });

  const sizeOptions = document.querySelectorAll(".size-option");
  sizeOptions.forEach((option) => {
    option.addEventListener("click", () => {
      sizeOptions.forEach((o) => o.classList.remove("selected"));
      option.classList.add("selected");
    });
  });
});
</script>

<template>
  <section class="product-page">
    <div class="product-center">
      <div class="sizes-addcart">
        <div class="sizes">
          <span class="size-option">L</span>
          <span class="size-option">M</span>
          <span class="size-option">S</span>
        </div>
        <button class="add-to-cart-btn">Add to Cart</button>
      </div>

      <div class="image-arrow-wrapper">
        <button id="prev-image" class="arrow-btn">
          <FontAwesomeIcon icon="fas fa-chevron-right" class="w-6 h-8" />
        </button>

        <div class="image-container">
          <img
            id="product-image"
            src="assets/images/WhatsApp_Image_2025-06-29_at_10.06.24_PM-removebg-preview.png"
            alt="Product Image"
          />
        </div>

        <button id="next-image" class="arrow-btn">
          <FontAwesomeIcon icon="fas fa-chevron-left" class="w-6 h-8" />
        </button>
      </div>
      <div class="product-details">
        <h2>white-Ivory</h2>
        <p>
          This stylish grey split zip jacket is made from high-quality
          materials. Perfect for your daily casual and smart wear.
        </p>
      </div>
    </div>
  </section>
  <div class="size-table-container">
    <h3>Size Guide</h3>
    <table class="size-table">
      <thead>
        <tr>
          <th>Size</th>
          <th>Width (cm)</th>
          <th>Length (cm)</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td title="Small - Fits chest up to 90cm">S</td>
          <td>52</td>
          <td>63</td>
        </tr>
        <tr>
          <td title="Medium - Fits chest up to 100cm">M</td>
          <td>55</td>
          <td>65</td>
        </tr>
        <tr>
          <td title="Large - Fits chest up to 110cm">L</td>
          <td>60</td>
          <td>65</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
.product-page {
  padding-top: 100px;
  padding-bottom: 60px;
  display: flex;
  justify-content: center;
}

.product-center {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: 30px;
  max-width: 1100px;
  padding: 0 20px;
  width: 100%;
  flex-wrap: nowrap;
}

.image-arrow-wrapper {
  display: flex;
  align-items: center;
  gap: 10px;
  justify-content: center;
}

.arrow-btn i {
  font-size: 18px;
}

.image-container {
  width: 280px;
  height: 400px;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  position: relative;
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 12px;
  transition: opacity 0.4s ease;
}

.fade-in {
  animation: fadeImage 0.4s ease;
}

@keyframes fadeImage {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.sizes-addcart {
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: flex-start;
}

.sizes {
  display: flex;
  gap: 10px;
}

.size-option {
  padding: 8px 14px;
  border: 1px solid #000;
  cursor: pointer;
  font-weight: bold;
  transition: 0.3s;
}

.size-option.selected,
.size-option:hover {
  background-color: black;
  color: white;
}

.add-to-cart-btn {
  background-color: black;
  color: white;
  padding: 10px 24px;
  border: none;
  font-size: 14px;
  cursor: pointer;
  font-weight: bold;
  transition: 0.3s;
}

.add-to-cart-btn:hover {
  background-color: #222;
}

.product-details {
  max-width: 280px;
}

.product-details h2 {
  font-size: 22px;
  margin-bottom: 14px;
  text-transform: uppercase;
}

.product-details p {
  font-size: 14px;
  line-height: 1.6;
  color: #444;
}
.size-table-container {
  margin-top: 40px;
  padding: 20px;
  text-align: center;
  overflow-x: auto;
}

.size-table-container h3 {
  font-size: 20px;
  margin-bottom: 20px;
  font-weight: bold;
  color: #0a0a23;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.size-table {
  width: 100%;
  max-width: 500px;
  margin: 0 auto;
  border-collapse: collapse;
  border: 1px solid #0a0a23;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  font-family: "Segoe UI", sans-serif;

  opacity: 0;
  transform: translateY(20px);
  animation: fadeInTable 0.8s ease-out forwards;
}

@keyframes fadeInTable {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.size-table thead th {
  background: #0a0a23;
  color: white;
  padding: 12px;
  font-size: 15px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.size-table thead i {
  margin-right: 6px;
  font-size: 13px;
}

.size-table tbody td {
  padding: 12px;
  border: 1px solid #ddd;
  font-size: 14px;
  color: #333;
  position: relative;
}

.size-table tbody tr:hover {
  background-color: #f2f2f2;
  transition: 0.3s;
}
</style>

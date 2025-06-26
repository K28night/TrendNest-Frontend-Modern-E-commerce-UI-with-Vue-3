<template>
  <div class="product-list">
    <div class="product-card" v-for="product in products" :key="product.id">
      <div class="product-image">
        <img :src="product.image" :alt="product.name" />
        <span v-if="product.sale" class="sale-tag">Sale</span>
      </div>
      <div class="product-info">
        <h3>{{ product.name }}</h3>
        <div class="price">
          <span class="current">Rs.{{ product.price }}</span>
          <span v-if="product.oldPrice" class="old">Rs.{{ product.oldPrice }}</span>
        </div>
        <p class="variants">+{{ product.variants }} more variants available</p>
      </div>
    </div>
  </div>
</template>
<script setup>
const products = [
  {
    id: 1,
    name: "Women Formal Shirt",
    price: "4,999.00",
    oldPrice: "5,999.00",
    variants: 1,
    sale: true,
    image: "/images/women-shirt.jpg"
  },
  {
    id: 2,
    name: "Cotton Shirt",
    price: "1,299.00",
    oldPrice: "1,599.00",
    variants: 1,
    sale: true,
    image: "/images/cotton-shirt.jpg"
  },
  {
    id: 3,
    name: "Silk Saree",
    price: "12,999.00",
    oldPrice: "16,999.00",
    variants: 1,
    sale: true,
    image: "/images/silk-saree.jpg"
  },
  {
    id: 4,
    name: "Festive Kurta",
    price: "999.00",
    variants: 0,
    sale: false,
    image: "/images/kurta.jpg"
  }
]
</script>
<style scoped>
.product-list {
  flex: 1;
  display: grid;
  padding-top: 80px; /* height of your header */
  padding-bottom: 150px; /* space for footer */
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 2rem;
  background-color: #f2f2f2;
}

.product-card {
  background-color: #fff;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
  transition: transform 0.3s ease;
}

.product-card:hover {
  transform: scale(1.05);
}

.product-image {
  position: relative;
  height: 260px;
  overflow: hidden;
}

.product-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.sale-tag {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: #00ADB5;
  color: #EEEEEE;
  padding: 4px 10px;
  font-size: 0.75rem;
  border-radius: 0 8px 0 8px;
  font-weight: bold;
}

.product-info {
  padding: 1rem;
}

.product-info h3 {
  margin: 0 0 0.5rem;
  font-size: 1.1rem;
  color: #222831;
}

.price {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.price .current {
  color: #00ADB5;
  font-weight: bold;
}

.price .old {
  color: gray;
  text-decoration: line-through;
  font-size: 0.9rem;
}

.variants {
  margin-top: 0.5rem;
  font-size: 0.8rem;
  color: #393E46;
}
</style>

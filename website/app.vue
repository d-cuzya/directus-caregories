<script setup>
import { ref } from 'vue';

const isOpen = ref(true); // Управление видимостью меню

const menuItems = [
  { name: 'Главная', path: '/' },
  { name: 'О нас', path: '/about' },
  { name: 'Контакты', path: '/contact' }
];
</script>

<template>
  <div class="sidebar" :class="{ open: isOpen }">
    <button class="toggle-btn" @click="isOpen = !isOpen">
      ☰
    </button>
    <nav v-if="isOpen">
      <ul>
        <li v-for="item in menuItems" :key="item.path">
          <a :href="item.path">{{ item.name }}</a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<style scoped>
.sidebar {
  width: 250px;
  height: 100vh;
  background: #2c3e50;
  color: white;
  position: fixed;
  left: 0;
  top: 0;
  transition: transform 0.3s ease;
}
.sidebar:not(.open) {
  transform: translateX(-100%);
}
.toggle-btn {
  position: absolute;
  top: 10px;
  right: -40px;
  background: #3498db;
  color: white;
  border: none;
  padding: 10px;
  cursor: pointer;
}
nav ul {
  list-style: none;
  padding: 20px;
}
nav ul li {
  margin: 15px 0;
}
nav ul li a {
  color: white;
  text-decoration: none;
}
</style>

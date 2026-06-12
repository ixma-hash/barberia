<script setup lang="ts">
import { ref } from 'vue'
import Citas from './componentes/citas.vue'
import Manicura from './componentes/manicura.vue'
import Login from './componentes/Login.vue'

const autenticado = ref(false)
const activeTab = ref<'barberia' | 'belleza'>('barberia')
</script>

<template>
  <Login v-if="!autenticado" @login="autenticado = true" />
  <div v-else class="app" :class="activeTab === 'belleza' ? 'manicura' : 'barberia'">
    <nav class="navbar">
      <span class="navbar-brand">SHADDAY BARBER</span>
      <div class="navbar-links">
        <button
          class="nav-btn"
          :class="{ active: activeTab === 'barberia' }"
          @click="activeTab = 'barberia'"
        >Barbería</button>
        <button
          class="nav-btn"
          :class="{ active: activeTab === 'belleza' }"
          @click="activeTab = 'belleza'"
        >Belleza</button>
      </div>
    </nav>
    <header class="app-header">
      <h1 class="app-title">{{ activeTab === 'barberia' ? 'Barbería' : 'Belleza' }}</h1>
      <p class="app-subtitle">{{ activeTab === 'barberia' ? 'Agenda tu cita con estilo' : 'Embellece tus manos y uñas' }}</p>
    </header>
    <Citas v-if="activeTab === 'barberia'" />
    <Manicura v-else />
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Inter:wght@300;400;500;600&family=Quicksand:wght@300;400;500;600&display=swap');

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background: #0d0d0d;
  min-height: 100vh;
  transition: background 0.4s;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1100px;
  margin: 0 auto 2rem;
  padding: 1rem 2rem;
  background: #1a1a1a;
  border-radius: 16px;
  border: 1px solid #2a2a2a;
  transition: all 0.4s;
}

.app.manicura .navbar {
  background: #ffffff;
  border-color: #fce4ec;
  box-shadow: 0 4px 24px rgba(242, 182, 200, 0.1);
}

.navbar-brand {
  font-family: 'Playfair Display', serif;
  font-size: 1.3rem;
  font-weight: 700;
  color: #d4a853;
  letter-spacing: 0.08em;
  transition: color 0.4s;
}

.app.manicura .navbar-brand {
  color: #e89ab0;
}

.navbar-links {
  display: flex;
  gap: 0.5rem;
}

.nav-btn {
  padding: 0.5rem 1.5rem;
  border: 1px solid #2a2a2a;
  border-radius: 50px;
  background: transparent;
  color: #888;
  font-size: 0.85rem;
  font-weight: 500;
  font-family: 'Inter', sans-serif;
  cursor: pointer;
  transition: all 0.3s;
}

.nav-btn:hover {
  color: #d4a853;
  border-color: #d4a853;
}

.nav-btn.active {
  background: #d4a853;
  color: #0d0d0d;
  border-color: #d4a853;
}

.app.manicura .nav-btn {
  border-color: #fce4ec;
  color: #c4a8b8;
  font-family: 'Quicksand', sans-serif;
}

.app.manicura .nav-btn:hover {
  color: #f2b6c8;
  border-color: #f2b6c8;
}

.app.manicura .nav-btn.active {
  background: linear-gradient(135deg, #f2b6c8, #e89ab0);
  color: #fff;
  border-color: transparent;
}

body:has(.app.manicura) {
  background: #fdf6f8;
}

.app {
  min-height: 100vh;
  padding: 2rem 1rem;
  transition: background 0.4s;
}

.app-header {
  text-align: center;
  margin-bottom: 2rem;
}

.app-title {
  font-family: 'Playfair Display', serif;
  font-size: 2.8rem;
  color: #d4a853;
  font-weight: 700;
  letter-spacing: 0.02em;
  transition: color 0.4s;
}

.app.manicura .app-title {
  color: #e89ab0;
}

.app-subtitle {
  font-family: 'Inter', sans-serif;
  color: #666;
  font-size: 1rem;
  margin-top: 0.25rem;
  transition: color 0.4s;
}

.app.manicura .app-subtitle {
  color: #c4a8b8;
  font-family: 'Quicksand', sans-serif;
}


</style>

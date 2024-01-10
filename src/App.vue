<script>
import { RouterLink, RouterView } from 'vue-router';
// import HelloWorld from './components/HelloWorld.vue'
import background from '@/assets/Image/weatherPic.gif';

export default {
  // 元件宣告
  components: {
    RouterView
  },
  data() {
    return {
      count:0,
      background,
    };
  },
}
</script>

<template>
  <!-- 觀察你的設計稿 把共用的部分放在此頁面 -->
  <header class="mb-[30px] text-[red]">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/calc">calc</RouterLink>
        <RouterLink to="/todolist">ToDoList</RouterLink>
        <RouterLink to="/pickupload">PickUpload</RouterLink>
        <RouterLink to="/weather">Weather</RouterLink>
  </header>
  <main :style="{backgroundImage:`url(${background})`}">
    <RouterView/>
    <div class="mb-[10px]">count:{{ count }}</div>
    <button @click="count++" class="mb-[30px]">++</button>
  </main>

  <!-- <RouterView /> -->
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style> 

<script>
import { RouterView } from 'vue-router';
// import HelloWorld from './components/HelloWorld.vue'
import background from '@/assets/Image/111.png';

export default {
  // 元件宣告
  components: {
    RouterView
  },
  data() {
    return {
      count: 0,
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

  <main :style="{backgroundImage: `url(${background})`}">
    <!-- <RouterView/> -->
    <div class="mb-[10px]">count:{{ count }}</div>
    <button @click="count++" class="mb-[30px]">++</button>
    <RouterView />
  </main>
  <footer>
  </footer>

</template>

<!-- scoped style只影響這支vue -->
<style scoped>
header {
  width: 100%;
  line-height: 1.5;
  min-height: 50px;
  max-height: 100vh;
  border-radius: 5px;
  background-color: black;
  color: rgb(236, 230, 219);
  margin-bottom: 10px;
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
main {
  width: 100%;
  padding: 0px 20px;
  background-size: cover;
  background-repeat: no-repeat;
  color: whitesmoke;
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

<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="header q-px-lg q-py-sm">
      <a href="#top" id="top">
        <img src="images/ico.png" alt="" style="width: 130px" />
      </a>
      <nav>
        <a href="#HOME">HOME</a>
        <a href="#MENU">MENU</a>
        <a href="#PRODUCTS">PRODUCTS</a>
        <a href="#ABOUT">ABOUT</a>
        <a href="#CONTACT-US">CONTACT US</a>
      </nav>

      <div class="icons">
        <q-icon
          name="person_outline"
          aria-hidden="true"
          color="primary"
          size="32px"
        />
        <q-icon
          name="shopping_cart"
          @click="addToCart(k2, topic)"
          color="primary"
          size="32px"
        />
      </div>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

defineOptions({
  name: "MainLayout",
});

const linksList = [
  {
    title: "Docs",
    caption: "quasar.dev",
    icon: "school",
    link: "https://quasar.dev",
  },
  {
    title: "Github",
    caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework",
  },
  {
    title: "Discord Chat Channel",
    caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev",
  },
  {
    title: "Forum",
    caption: "forum.quasar.dev",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev",
  },
  {
    title: "Twitter",
    caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev",
  },
  {
    title: "Facebook",
    caption: "@QuasarFramework",
    icon: "public",
    link: "https://facebook.quasar.dev",
  },
  {
    title: "Quasar Awesome",
    caption: "Community Quasar projects",
    icon: "favorite",
    link: "https://awesome.quasar.dev",
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  outline: none;
  list-style: none;
  text-decoration: none;
  font-family: "Poppins", sans-serif;
  font-optical-sizing: auto;
  font-style: normal;
  border: none;
}

:root {
  --bg-color: #000000;
  --btn: #cb863f;
  --border: #6c4620;
  --white: #ffffff;
  --text-gray: #9e9e9e;
  --bg-gray: #424242;
  --bg-s-gray: #616161;
}
body {
  background-color: var(--bg-color);
  position: relative;
  overflow: auto;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  /* padding: 20px 10px; */
  padding-bottom: 0;
  border-bottom-right-radius: 5px;
  border-bottom-left-radius: 5px;
  background-color: var(--bg-gray) ;
}

.header nav {
  display: flex;
  gap: 40px;
  font-size: 20px;
}

.header nav a {
  color: var(--white);
  transition: 0.3s;
  text-decoration: none;
}
.header nav a:hover {
  color: var(--btn);
}

.header .icons {
  display: flex;
  gap: 50px;
}

.header .icons .fa-shopping-basket {
  font-size: 28px;
  color: var(--border);
  transition: 0.3s;
  cursor: pointer;
}
.header .icons .fa-shopping-basket:hover {
  color: var(--btn);
}

.header .icons .fa-user {
  font-size: 28px;
  color: var(--btn);
  transition: 0.3s;
  cursor: pointer;
}
.header .icons .fa-user:hover {
  color: var(--border);
}
</style>

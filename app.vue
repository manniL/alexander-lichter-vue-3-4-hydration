<script setup lang="ts">
type Link = { name: string; link: string; }
const list = ref<Link[]>();
list.value = generateRandomLinks()

function generateRandomLinks() {
  const links: Link[] = [];

  for (let i = 0; i < 10; i++) {
    const link = generateRandomLink();
    links.push({
      name: "data" + i,
      link: link,
    });
  }
  return links;
}

function generateRandomLink() {
  const characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789";
  const length = 10;
  let link = "";

  for (let i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * characters.length);
    link += characters[randomIndex];
  }

  return `https://example.com/${link}`;
}
</script>

<template>
  <ul>
    <li v-for="item in list" :key="item.name">
      <NuxtLink :to="item.link">{{ item.name }}:{{ item.link }}</NuxtLink>
    </li>
  </ul>
</template>
<template>
  <nav class="bg-yellow-500 text-white">
    <div class="container flex justify-center mx-auto">
      <div class="flex item-center">
        <router-link to='/calculator' class="inline-block px-16 py-4 transition-colors hover:bg-yellow-400 duration-300">
          Calculators
        </router-link>
        <router-link to='/todos' class="inline-block px-16 py-4 transition-colors hover:bg-yellow-400 duration-300">
          Todo
        </router-link>
      </div>
    </div>
  </nav>
  <router-view/>
</template>
<style>
  body {
    background: #111f2e;
  }
</style>
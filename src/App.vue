<script setup>
import {ref} from 'vue'
import Logo from './assets/img/logo.svg'

const menu = ['buy crypto', 'markets', 'trade', 'finance', 'learn', 'support', 'more']
const target = ['Popular assets', 'New assets', 'Gains ranking', 'Turnover ranking']
const fieldName = ['Asset', 'Last price', 'Today\'s change', 'Chart', 'Trade']
const crypto = ['BTC', '46000$', '+0.35%', 'chart', 'trade']
const crypto2 = ['ETH', '4300$', '+0.25%', 'chart', 'trade']
const url = 'https://api.alternative.me/v2/ticker/?limit=10'
const result = ref(null)

fetch(url)
    .then(response => response.json())
    .then(data => result.value = data)
</script>

<template>
  <main>
    <div class="w-full min-h-screen font-sans text-gray-300">
      <div class="bg-gradient-to-r from-[#000000] to-[#0B0033]">
        <div class="px-6 mx-auto max-w-6xl">
          <div class="flex justify-between items-center py-10">
            <div class="cursor-pointer">
              <Logo />
            </div>
            <nav class="flex items-center space-x-10">
              <a
                  v-for="item in menu"
                  class="hover:text-white"
                  href="#"
              >
                {{ item }}
              </a>
            </nav>
          </div>
          <div class="flex justify-center items-center space-x-10 py-10">
            <a
                v-for="item in target"
                class="hover:text-white"
                href="#"
            >
              {{ item }}
            </a>
          </div>
          <div class="flex justify-center items-center text-xs text-gray-400 space-x-10 py-10">
            <ul
                class="px-10"
                v-for="(item, index) in fieldName"
            >
              {{ item }}
              <li class="text-base text-white mt-10">
                {{ crypto[index] }}
              </li>
              <li class="text-base text-white my-5">
                {{ crypto2[index] }}
              </li>
            </ul>
          </div>
          <div class="flex justify-center items-center text-xs text-gray-400 space-x-10 py-10">
            {{ result }}
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>

</style>

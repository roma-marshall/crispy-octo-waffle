<script setup>
import {ref} from 'vue'
import Logo from './assets/img/logo.svg'

const menu = ['buy crypto', 'markets', 'trade', 'finance', 'learn', 'support', 'more']
const target = ['Popular assets', 'New assets', 'Gains ranking', 'Turnover ranking']
const fieldName = ['Asset', 'Last price', 'Today\'s change', 'Chart', 'Trade']
const url = 'https://api.alternative.me/v2/ticker/?limit=9'
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
              <Logo/>
            </div>
            <nav class="hidden md:flex md:items-center md:space-x-10">
              <a
                  v-for="item in menu"
                  class="hover:text-white"
                  href="#"
              >
                {{ item }}
              </a>
            </nav>
            <button class="p-4 md:hidden">
              <span class="w-6 h-6 text-white text-3xl line-through">_</span>
            </button>
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
          <div class="md:flex md:justify-center md:items-center md:space-x-10 text-xs text-gray-400 py-10">
            <div
                v-for="(item, index) in fieldName"
                class="px-10 pb-10"
            >
              {{ item }}
              <ul
                  v-for="(item, i, key) in result['data']"
                  class="text-base text-white mt-10"
              >
                <li v-if="index === 0 && key !== 3">
                  {{ item['symbol'] }}
                </li>
                <li v-if="index === 1 && key !== 3">
                  {{ item['quotes']['USD']['price'] }}$
                </li>
                <li v-if="index === 2 && key !== 3">
                  <span
                      v-if="item['quotes']['USD']['percentage_change_24h'] >= 0"
                      class="text-green-500"
                  >
                    {{ item['quotes']['USD']['percentage_change_24h'].toFixed(2) }}%
                  </span>
                  <span
                      v-else
                      class="text-red-500"
                  >
                    {{ item['quotes']['USD']['percentage_change_24h'].toFixed(2) }}%
                  </span>
                </li>
                <li v-if="index === 3 && key !== 3">
                  -
                </li>
                <li v-if="index === 4 && key !== 3">
                  <a href="#" class="hover:text-gray-300 cursor-pointer">Buy</a>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>

</style>

<script setup>
import {ref} from 'vue'
import Logo from './assets/img/logo.svg'

const menu = ['buy crypto', 'markets', 'trade', 'finance', 'learn', 'support', 'more']
const target = ['Popular assets', 'New assets', 'Gains ranking', 'Turnover ranking']
const fieldName = ['Asset', 'Last price', 'Today\'s change', 'Chart', 'Trade']
const crypto = ['BTC', '46000$', '+0.35%', 'chart', 'trade']
const crypto2 = ['ETH', '4300$', '+0.25%', 'chart', 'trade']
const url = 'https://api.alternative.me/v2/ticker/?limit=8'
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
            <div
                v-for="(item, index) in fieldName"
                class="px-10 pb-10"
            >
              {{ item }}
              <ul
                  v-for="(item, key) in result['data']"
                  class="text-base text-white mt-10"
              >
                <li v-if="index === 0 && key !== 3">
                  {{ item['symbol'] }}
                </li>
                <li v-if="index === 1 && key !== 3">
                  {{ item['quotes']['USD']['price'] }}$
                </li>
                <li v-if="index === 2 && key !== 3">
                  {{ item['quotes']['USD']['percentage_change_24h'].toFixed(2) }}%
                </li>
                <li v-if="index === 3 && key !== 3">
                  none
                </li>
                <li v-if="index === 4 && key !== 3">
                  none
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

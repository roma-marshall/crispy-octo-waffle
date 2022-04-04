<script setup>
const menu = ['buy crypto', 'markets', 'trade', 'finance', 'learn', 'support', 'more']
const target = ['Popular assets', 'New assets', 'Gains ranking', 'Turnover ranking']
const fieldName = ['Asset', 'Last price', 'Today\'s change', 'Chart', 'Trade']
const crypto = ['BTC', '46000$', '+0.35%', 'chart', 'trade']
const crypto2 = ['ETH', '4300$', '+0.25%', 'chart', 'trade']
</script>

<template>
  <main>
    <div class="w-full min-h-screen font-sans text-gray-300">
      <div class="bg-gradient-to-r from-[#000000] to-[#0B0033]">
        <div class="px-6 mx-auto max-w-6xl">
          <div class="flex justify-between items-center py-10">
            <div class="cursor-pointer">
              <svg version="1.2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 161 48" width="161" height="48">
                <path fill="#fff" d="m42.3 43.2v-2l86.7 0.3v2z"/>
                <text style="transform: matrix(1,0,0,1,42,36)">
                  <tspan x="0" y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">E
                  </tspan>
                  <tspan y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">X</tspan>
                  <tspan y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">c</tspan>
                  <tspan y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">h</tspan>
                  <tspan y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">a</tspan>
                  <tspan y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">n</tspan>
                  <tspan y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">g</tspan>
                  <tspan y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">e</tspan>
                  <tspan y="0" font-size="24px" fill="#ffffff" font-weight="400" font-family="DejaVuSans">
                  </tspan>
                </text>
                <path fill="none" stroke="#ffffff" stroke-width="3" d="m2 17h25v25h-25z"/>
                <path fill="none" stroke="#ffffff" stroke-width="3" d="m14 5h25v25h-25z"/>
              </svg>
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
            <ul v-for="(item, index) in fieldName">
              {{ item }}
              <li>
                {{ crypto[index] }}
              </li>
              <li>
                {{ crypto2[index] }}
              </li>
            </ul>
          </div>

        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>

</style>

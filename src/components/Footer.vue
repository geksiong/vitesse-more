<script setup lang="ts">
import { isDark, toggleDark } from '~/logic'

const { t, availableLocales, locale } = useI18n()

const toggleLocales = () => {
  // change to some real logic
  const locales = availableLocales
  locale.value = locales[(locales.indexOf(locale.value) + 1) % locales.length]
}
</script>

<template>
  <nav class="text-3xl mt-6 bg-white" :class="{ dark: isDark }">
    <router-link class="icon-btn mx-2" to="/" :title="t('button.home')">
      <mdi-human-scooter />
    </router-link>

    <button class="icon-btn mx-2 !outline-none" :title="t('button.toggle_dark')" @click="toggleDark()">
      <carbon-moon v-if="isDark" />
      <carbon-sun v-else />
    </button>

    <a class="icon-btn mx-2" :title="t('button.toggle_langs')" @click="toggleLocales">
      <carbon-language />
    </a>

    <router-link class="icon-btn mx-2" to="/about" :title="t('button.about')">
      <carbon-dicom-overlay />
    </router-link>

    <a
      class="icon-btn mx-2"
      rel="noreferrer"
      href="https://github.com/geksiong/vitesse-more"
      target="_blank"
      title="GitHub"
    >
      <carbon-logo-github />
    </a>
  </nav>
</template>

<style scoped>
.dark {
  background-color: #121224;
}
</style>

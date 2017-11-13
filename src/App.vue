<template>
  <div id="app">
    <a href="/" class="app-logo text-center">
      <img src="./assets/img/logo.png" alt="" class="app-logo__img" />
    </a>
    <currency-exchange />
  </div>
</template>

<script>
import CurrencyExchange from '@/components/CurrencyExchange'

export default {
  name: 'app',
  components: {
    CurrencyExchange
  }
}
</script>

<style src="./assets/scss/app.scss"></style>
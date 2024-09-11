<script setup>
import Close from '../icons/Close.vue'
import { ref } from 'vue'

const searchMovie = ref('')
</script>

<template>
  <div class="search">
    <form class="search-form" @submit.prevent="">
      <input
        type="text"
        class="search-input"
        placeholder="Введите название"
        v-model="searchMovie"
      />
      <button><Close /></button>
      <button>Найти</button>
    </form>
  </div>
</template>

<style lang="scss" scoped>
@import '../../assets/styles/main.scss';
.search {
  display: flex;
  align-items: center;
  justify-content: center;
  .search-form {
    .search-input {
      font-size: 20px;
      color: $red;
      padding: 5px;
      height: 40px;
      width: 500px;
      border: 5px solid $red;
      &.focus {
        border: none;
        outline: none;
      }
    }
  }
}
</style>

<script setup>
import ListMovie from './components/movie/ListMovie.vue'
import SearchMovies from './components/search/SearchMovies.vue'
import { useMovieStore } from './stores/MovieStore'

const movieStore = useMovieStore()

const setTab = (id) => {
  movieStore.setActiveTab(id)
}
</script>

<template>
  <div class="app">
    <div class="container">
      <header class="header">
        <img src="./assets/img/logo.png" alt="logo" class="header-logo" />
      </header>
      <div class="tabs">
        <button
          :class="['btn-white', { btn_white: movieStore.activeTab === 1 }]"
          @click="setTab(1)"
        >
          Любимые
        </button>
        <button :class="['btn-red', { btn_red: movieStore.activeTab === 2 }]" @click="setTab(2)">
          Поиск
        </button>
      </div>
      <main class="main">
        <ListMovie v-if="movieStore.activeTab === 1" />
        <div v-else class="search">
          <SearchMovies />
        </div>
      </main>
    </div>
  </div>
</template>

<style lang="scss">
@import './assets/styles/main.scss';

.app {
  background-color: $black;
  .container {
    max-width: 1440px;
    padding: 25px 0 0 0;
    margin: 0 auto;
    min-height: 100vh;
    .tabs {
      display: flex;
      justify-content: center;
      margin-top: 30px;
    }
    .header {
      display: flex;
      justify-content: center;
      padding-top: 10px;
      .header-logo {
        max-width: 100px;
      }
    }
    .main {
      .movies {
        color: $white;
      }
    }
  }
}
.btn-white {
  @include btn-white;
}
.btn-red {
  @include btn-red;
  margin-right: 10px;
}
.btn_watched {
  @include btn-watched;
}
.btn-search {
  @include btn-search;
  margin-left: 10px;
}
.btn_favorite {
  @include btn_favorite;
}
</style>

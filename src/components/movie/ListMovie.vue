<script setup>
import ListWatchedMovies from './ListWatchedMovies.vue'
import ListItemMovie from './ListItemMovie.vue'
import { useMovieStore } from '../../stores/MovieStore'

const movieStore = useMovieStore()
</script>

<template>
  <div v-if="movieStore.watchedMovies.length >= 1">
    <h2 class="movies-list__title2">Мои любимые фильмы</h2>
    <span class="movies-list__total"
      >Количество ваших фильмов: {{ movieStore.watchedMovies.length }}
    </span>
    <ul class="movies-list__watched">
      <ListWatchedMovies
        v-for="movieWatched in movieStore.watchedMovies"
        :movieWatched="movieWatched"
        :key="movieWatched.id"
      />
    </ul>
    <span class="separation"></span>
  </div>
  <h2 class="movies-list__title2">Популярные фильмы</h2>
  <ul class="movies-list">
    <ListItemMovie v-for="movie in movieStore.movies" :movie="movie" :key="movie.id" />
  </ul>
</template>

<style lang="scss" scoped>
@import '../../assets/styles/main.scss';

.movies-list__watched {
  display: flex;
  flex-wrap: wrap;
  margin: 0;
  padding: 0;
}
.separation {
  display: block;
  border: 1px solid $white;
}
.movies-list__title2 {
  color: $white;
  font-size: 44px;
}
.movies-list {
  display: flex;
  flex-wrap: wrap;
  margin: 0;
  padding: 0;
}

.movies-list__total {
  color: $red;
  font-weight: 500;
  font-size: 24px;
}
</style>

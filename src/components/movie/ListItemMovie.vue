<script setup>
import { useMovieStore } from '@/stores/MovieStore'

const movieStore = useMovieStore()
const props = defineProps({
  movie: {
    type: Object,
    required: true,
    default: () => {}
  }
})
</script>

<template>
  <li class="movie-item">
    <img
      :src="`https://image.tmdb.org/t/p/w300_and_h450_bestv2${movie.poster_path}`"
      :alt="movie.original_title"
      class="movie-img"
    />
    <div class="movie-item__block">
      <h3 class="movie-item__name">
        {{ movie.original_title }}
      </h3>
      <div class="movie-item__description">
        <span class="movie-item__date">{{ movie.release_date }}</span>
        <p class="movie-overview">{{ movie.overview }}</p>
      </div>
      <div class="movie-item__btn">
        <button
          :class="['btn-red', { btn_watched: movie.activeTab === 1 }]"
          @click="movieStore.toggleWatched(movie.id)"
        >
          <span v-if="!movie.isWatched">Смотреть</span>
          <span v-else>Убрать</span>
        </button>
        <button class="btn-white" @click="movieStore.deleteMovie(movie.id)">Удалить</button>
      </div>
    </div>
  </li>
</template>

<style lang="scss" scoped>
@import '../../assets/styles/main.scss';

.movie-item {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  margin: 20px 20px 20px 0;
  color: $white;
  .movie-img {
    width: 200px;
  }
  .movie-item__block {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-end;
    margin-left: 15px;
    .movie-item__name {
      margin: 0 0 30px 0;
      font-size: 28px;
      font-weight: 500;
    }
    .movie-item__description {
      display: flex;
      flex-direction: column;
      justify-content: f;
      .movie-overview {
        width: 400px;
      }
    }
    .movie-item__btn {
      display: flex;
      align-items: center;
      justify-content: center;
    }
  }
}
</style>

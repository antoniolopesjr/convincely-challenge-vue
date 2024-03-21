<template>
  <div>
    <div class="MovieCard_Container">
      <div class="Movie_Bg">
        <img :src="moviePseudoImage" alt="movie.title" />
      </div>
      <div class="Movie-info">
        <h2>{{ movie.name }}</h2>
        <p>{{ movie.runtimeInMinutes }} min</p>
        <p>{{ movie.academyAwardNominations }} nominations</p>
        <div class="Movie_values">
          <div>{{ movie.budgetInMillions }}m</div>
          <div>{{ movie.boxOfficeRevenueInMillions }}m</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "MovieCard",
  data() {
    return {
      moviePseudoImage: 'https://static.thenounproject.com/png/4050454-200.png'
    };
  },
  props: {
    movie: {
      type: Object,
      required: true,
    },
  },
}
</script>
<style lang="scss">
.MovieCard_Container {
  display: flex;
  flex-direction: column;
  min-width: 300px;
  border: 1px solid #000;
  max-height: 435px;
  min-height: 435px;
}
.Movie_Bg {
  height: 200px;
}
.Movie-info {
  display: flex;
  flex-direction: column;
  padding: 10px;
  height: 100%;
}
.Movie_values {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>
<template>
	<div class="main-container">
		<div class="upper-container">
			<div>
				<input v-model="searchTerm" type="text" placeholder="Filter movies by name" />
				<select v-model="selectedSorting">
					<option disabled value="">Escolha um item</option>
					<option>Sort by budget</option>
					<option>ASC</option>
					<option>DESC</option>
				</select>
			</div>
		</div>
		<div v-if="filteredMovieList.length > 0" class="Movies_grid_container">
			<div v-for="movie in filteredMovieList" :key="movie._id">
				<MovieCard :movie="movie" />
			</div>
		</div>
	</div>
</template>
<script>
import MovieCard from './MovieCard.vue';
export default {
	name: 'MoviesList',
	components: {
		MovieCard
	},
	data() {
		return {
			sortingOptions: ['Sort by budget', 'ASC', 'DESC'],
			selectedSorting: 'Sort by budget',
      searchTerm: '',
      filteredMovieList: []
		};
	},
	props: {
		moviesList: {
			type: Array,
			required: false
		}
	},
  watch: {
    searchTerm(newVal) {
      this.filterByTerm(newVal);
    },
    moviesList(newVal) {
      this.filteredMovieList = newVal;
    }
  },
  methods: {
    filterByTerm(term) {
      if (term && term.length >= 1) {
        this.filteredMovieList = this.moviesList.filter(movie => movie.name.toLowerCase().includes(this.searchTerm.toLowerCase()))
      } else if (!term) {
        this.filteredMovieList = this.moviesList;
      }
    }
  },
};
</script>
<style lang="scss">
.main-container {
	width: 100%;
}
.upper-container {
	display: flex;
	flex-direction: row;
	justify-content: flex-end;
	height: 190px;
	padding: 80px;
}

.Movies_grid_container {
	display: grid;
	grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
	grid-gap: 50px;
  padding: 100px;
}
</style>

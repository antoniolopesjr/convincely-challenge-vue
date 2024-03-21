<script>
import axios from 'axios';
import MoviesList from './components/MoviesList.vue';

const url = 'https://the-one-api.dev/v2/movie';
const apiToken = 'SlauvktIL11a0f5QoDXy';

export default {
	data() {
		return {
			moviesList: []
		};
	},
	components: {
		MoviesList
	},
	async created() {
		await this.getMovies();
	},
	methods: {
		async getMovies() {
			await axios
				.get(url, {
					headers: {
						Authorization: `Bearer ${apiToken}`
					}
				})
				.then((response) => {
					this.moviesList = response.data.docs;
				});
		}
	}
};
</script>

<template>
	<MoviesList v-if="moviesList" :moviesList="moviesList" />
</template>

<style lang="scss">
@import './assets/base.scss';
</style>

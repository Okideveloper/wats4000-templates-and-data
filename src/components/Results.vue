<template>
  <div class="results">
    <h1>
      Top Movies from the 20
      <sup>th</sup> Century
    </h1>
    <p class="search-meta">
      <span class="current-page">
        <b>Current Page:</b> 1
      </span>

      <span class="total-pages">
        <b>Pages:</b>
        {{total_pages}}
      </span>

      <span class="total-results">
        <b>Count:</b>
        {{total_results}}
      </span>
    </p>

    <ul>
      <li class="movie-item" v-for="(result,id) in results" :key="id">
        <!-- below making the poster image appear from source site using attribute poster_path-->
        <img
          :src="'https://image.tmdb.org/t/p/w150_and_h225_bestv2/' + result.poster_path"
          :alt="result.original_title"
          class="poster-image"
        >
        <!-- using the v-bind ({}) we will aquire accurate results for each movie -->
        <h2 class="title">
          <a :href="'https://www.themoviedb.org/movie/' + result.id">{{result.original_title}}</a>
        </h2>

        <div class="ratings">
          <span
            class="rating-category critics-choice"
            v-if="result.vote_average > 8"
          >Critic's Choice</span>
          <span
            class="rating-category well-liked"
            v-if="result.vote_average > 7 && result.vote_average <=8"
          >Well Liked</span>
          <span class="rating-category stinker" v-if="result.vote_average < 7">Stinker</span>
          <!-- using the v-bind ({}) we will aquire accurate results for each movie -->
          <h5 class="vote-average">{{result.vote_average}} with
          <span class="vote-count">{{result.vote_count}}</span> votes</h5>
        </div>
        <p class="overview">
          <!-- Below using the mustache (v-bind) we will aquire the data summary for each movie -->
          {{result.overview}}
        </p>
        <p
          class="release-date"
        >Original Release: {{new Date (result.release_date).toLocaleDateString("en-US")}}</p>
        <ul class="genre-list">
          <h5 class="genre-caption">Genre</h5>

          <li v-for="(genre,index) in result.genres" :key="index">{{genre}}</li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
import apiresults from "../assets/apiresults.js";
export default {
  data() {
    return apiresults;
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  margin: 0 0 1rem 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
.search-meta {
  text-align: right;
}
.movie-item {
  margin: 10px 0;
  padding: 2rem;
  box-shadow: 4px 4px 10px rgba(0, 0, 0, 0.2);
}
.movie-item img {
  float: left;
  margin-right: 1rem;
}
.release-date {
  font-weight: 600;
  font-size: 12px;
  color: #333;
}
.rating-category {
  font-size: 12px;
  color: #fff;
  font-weight: 800;
  background: #ccc;
  padding: 0.5rem;
  border-radius: 4px;
}
.rating-category.critics-choice {
  background: goldenrod;
}
.rating-category.well-liked {
  background: green;
}
.rating-category.stinker {
  background: brown;
}
.genre-list li {
  border-radius: 4px;
  background: rgb(58, 109, 92);
  color: #fff;
  font-weight: 800;
  font-size: 12px;
  padding: 0.5rem;
  display: inline-block;
  margin-right: 10px;
}
a {
  color: #42b983;
}
</style>
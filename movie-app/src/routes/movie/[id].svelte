<script context="module">
  export async function load({ fetch, params }) {
    const res = await fetch(
      `https://api.themoviedb.org/3/movie/${params.id}?api_key=0c130c34bc7de50f48c687c8e7e4523e&language=en-US`
    );
    const movieDetails = await res.json();
    if (res.ok) {
      return {
        props: { movieDetails },
      };
    }
  }
</script>

<script>
  export let movieDetails;
</script>

<div class="movie-details">
  <div class="img-container">
    <img
      src={"https://image.tmdb.org/t/p/original" + movieDetails.backdrop_path}
      alt={movieDetails.title}
    />
  </div>
  <div class="text-container">
    <h1>{movieDetails.title}</h1>
    <p class="overview">
      {movieDetails.overview}
    </p>
    <p>
      <span>Release Date</span>
      {movieDetails.release_date}
      <br />
      <span>Budget:</span>
      {movieDetails.budget} <br />
      <span>Rating:</span>
      {movieDetails.vote_average}<br />
      <span>Runtime:</span>
      {movieDetails.runtime}mins
    </p>
  </div>
</div>

<style>
  h1 {
    padding: 1rem 0rem 2rem;
  }
  p {
    padding: 1rem 0rem;
  }
  .img-container {
    width: 100%;
  }
  img {
    width: 100%;
    border-radius: 10px;
  }
  .movie-details {
    margin: 2rem 20%;
  }
  span {
    font-weight: bold;
  }
</style>

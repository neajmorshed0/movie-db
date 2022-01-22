<script context="module">
  export async function load({ fetch }) {
    const res = await fetch(
      `https://api.themoviedb.org/3/movie/popular?api_key=0c130c34bc7de50f48c687c8e7e4523e`
    );
    const data = await res.json();
    if (res.ok) {
      return {
        props: { popular: data.results },
      };
    }
  }
</script>

<script>
  import PopularMovies from "../components/PopularMovies.svelte";
  export let popular;
  import global from "../global.css";
</script>

<section>
  <PopularMovies {popular} />
</section>

<style>
</style>

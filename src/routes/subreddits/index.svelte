<script>
  import {onMount} from 'svelte'

  let API = "http://localhost:8080/burogu/api/subreddit/v1/"
  let subreddits = []
  onMount(async () => {
    subreddits = await fetch(API)
            .then(x => x.json())
            .then(value => {
                      console.log(value)
                      return value
                    }
            )
  })

</script>

<style>
  ul {
    margin: 0 0 1em 0;
    line-height: 1.5;
  }

  .card {
    /* Add shadows to create the "card" effect */
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    transition: 0.3s;
  }

  /* On mouse-over, add a deeper shadow */
  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
  }

  /* Add some padding inside the card container */
  .container {
    padding: 2px 16px;
    margin-bottom: 30px;
  }
</style>

<svelte:head>
  <title>Blog</title>
</svelte:head>

<h1>Top Communities</h1>

<ul>
    {#each subreddits as subreddit}
    <!-- we're using the non-standard `rel=prefetch` attribute to
				tell Sapper to load the data for the page as soon as
				the user hovers over the link or taps it, instead of
				waiting for the 'click' event -->
      <div class="card">
        <div class="container">
          <a rel="prefetch" href="blog/">
            <h4><b>{subreddit.type == 'u' ? 'u/' : 'r/'}{subreddit.name}</b></h4>
          </a>
        </div>
      </div>
    {/each}
</ul>

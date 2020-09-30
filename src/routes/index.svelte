<script>
    import {onMount} from 'svelte'
    import Post from "../components/Post.svelte";

    let API = "http://localhost:8080/burogu/api/posts/v1/"
    let posts = []
    onMount(async () => {
        posts = await fetch(API)
                .then(x => x.json())
                .then(value => {
                            console.log(value)
                            return value
                        }
                )
    })
</script>

<svelte:head>
    <title>Burogu | Posts</title>
</svelte:head>

<div class="btn-group mb-4 w-100" role="group" aria-label="Basic example">
    <button type="button" class="btn btn-secondary">Recent</button>
    <button type="button" class="btn btn-secondary">Popular</button>
</div>

{#each posts as post}
    <Post post={post}/>
{/each}

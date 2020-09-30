<script>
    import {onMount} from 'svelte'
    import Post from "../../components/Post.svelte";

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

<style>
    ul {
        margin: 0 0 1em 0;
        line-height: 1.5;
    }
</style>

<svelte:head>
    <title>Blog</title>
</svelte:head>

<h1>Recent posts</h1>

<ul>
    {#each posts as post}
        <Post title={post.title} comment={post.description} posted="3"/>
    {/each}
</ul>

<script>
    import moment from "moment";

    export let post = {
        title,
        description,
        subredditName,
        subredditType,
        author,
        createdAt,
        upVotes,
        downVotes
    }
    const {title, description, subredditName, subredditType, author, createdAt, upVotes, downVotes} = post;
    const posted = moment(createdAt).fromNow();
    console.log(moment.locale())
</script>

<style>
    .actions-container {
        width: 5%;
        background-color: antiquewhite;
    }
</style>

<div class="card mb-3">

    <div class="card-header">
        <small class="text-muted">
            {subredditType}/{subredditName} by u/{author}
        </small>
    </div>
    <div class="d-flex">
        <div class="card-body">
            <h5 class="card-title">{title}</h5>
            <p class="card-text">{description}</p>
            <p class="card-text"><small class="text-muted">Created {posted}</small></p>
        </div>
        <div class="actions-container d-flex flex-column">
            <button type="button" class="close">
                <span aria-hidden="true">&times;</span>
            </button>
        </div>
    </div>
</div>

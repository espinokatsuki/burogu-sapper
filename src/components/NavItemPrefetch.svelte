<script>
    export let navTitle;
    export let page;
    export let segment;
</script>

<li class="nav-item">
    <a rel=prefetch class="nav-link" aria-current="{segment === {page} ? 'page' : undefined}" href={page}>
        {navTitle}
    </a>
</li>

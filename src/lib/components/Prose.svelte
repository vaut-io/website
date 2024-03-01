<div>
    <slot />
</div>

<style>
    div {
        max-inline-size: var(--measure);
    }
    div :global(*) + :global(*) {
        margin-block-start: 1em;
    }
    div :global(h1) {
        font-size: var(--t5);
    }
    div :global(h2) {
        font-size: var(--t3);
    }
    div :global(h3) {
        font-size: var(--t2);
    }
    div :global(h4) {
        font-size: var(--t1);
    }
    div :global(p),
    div :global(li) {
        font-size: var(--t0);
    }
</style>

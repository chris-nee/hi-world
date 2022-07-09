<script>
    import Summary from '../components/Summary/Summary.svelte'

    let items = [{
            path: 'post-1',
            title: 'First post',
            offset: 1
        },
    ]

</script>

<home>
    <h1> Blog </h1>
    {#each items as {path, title, offset}, i}
            <Summary {path} {title} {i} {offset}/>
    {/each}
</home>

<style>
</style>

<script>
    import { Link } from "svelte-navigator";

	export let path;
	export let title;
	export let i;
	export let offset;

</script>

<article>
	<span>{i + offset + 1}</span>
    <h2><Link to={path}>{title}</Link></h2>
	<p class="meta"></p>
</article>

<style>
	article {
		position: relative;
		padding: 0 0 0 2em;
		border-bottom: 1px solid #eee;
	}

	h2 {
		font-size: 1em;
		margin: 0.5em 0;
	}

	span {
		position: absolute;
		left: 0;
	}

	a {
		color: #333;
	}
</style>

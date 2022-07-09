<script>
    import { onMount } from 'svelte'
    import { Link, Router, Route } from "svelte-navigator";
    import Blog from './pages/Blog.svelte'
    import About from './pages/About.svelte'
    import BlogPost1 from './posts/Post-1.svelte'
	export let name;

	async function hashchange() {
		// the poor man's router!
		const path = window.location.hash.slice(1);

		if (path.startsWith('/post')) {
			const id = path.slice(6);
			item = await fetch(`https://node-hnapi.herokuapp.com/item/${id}`).then(r => r.json());

			window.scrollTo(0,0);
		} else if (path.startsWith('/top')) {
			page = +path.slice(5);
			item = null;
		} else {
			window.location.hash = '/top/1';
		}
	}

	onMount(hashchange);
</script>

<svelte:window on:hashchange={hashchange}/>

<Router>
    <main>
	    <h1>Hi {name}!</h1>
        <nav>
            <Link to='blog'>Blog</Link> |
            <Link to='/'>About</Link> |
        </nav>
        <Route path="/blog">
            <Blog/>
        </Route>
        <Route path="/">
            <About/>
        </Route>
        <Route path="/blog/post-1">
            <BlogPost1/>
        </Route>
    </main>
</Router>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

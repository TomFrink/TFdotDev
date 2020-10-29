<script>
	import { onMount } from 'svelte';

	export let project = [];
	export let name;
	export let tech;
	export let type;
	export let website;
	export let github;

	onMount(async () => {
		const res = await fetch(`https://api.github.com/repos/tomfrink/stoicpage`);
		project = await res.json();
	});
</script>

<style> 
	.card {
		/* Make it card-like */
	  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
	  padding: 16px;
	  text-align: center;
	  background-color: honeydew;
	  /* In-Card Grid */
	  display: grid;
	  grid-template-columns: 1fr 1fr 1fr 1fr;
	  grid-template-rows: 1fr 1fr 1fr;
	  gap: 1px 1px;
	  grid-template-areas: "image image title title" "image image info info" "image image links links";
	  align-content: space-between;
	}
	/* List Styles */
	.info, .links > ul , li{
		display: inline;
		list-style-type: none;
	}
	.image > img{
		max-width: 100%;
	}
	/* Grid Elements */
	.image { grid-area: image; }

	.title { grid-area: title; align-self: center; }

	.info { grid-area: info; }

	.links { grid-area: links; }
</style>
	<!-- Option A -->
<div class="card">
	<div class="image">
		<img alt="Stoic Page" src="\screenshots\stoic.page_screenshot.png" />
		</div>
	<div class="title">
		<h2>
			<code>{name}</code> is a {type} project
		</h2>
		</div>
	<div class="info">
		<h2>Tech used:</h2>
			<ul>
			{#each tech as {packageName, id}, i}
			<li target="_blank">
				<a href="https://www.npmjs.com/package/{id}">
					{packageName}
				</a>
			</li>
			{/each}
			</ul>
		</div>
	<div class="links">
		<a href={website}>Click Here</a> to see {name}
		<br />
		<a href= 'https://github.com/TomFrink/{github}'>Click Here</a> to see {name}'s code on GitHub
		</div> 
</div>
<hr>
<!-- Option B -->
<div class="card">
	<div class="image">
				<img alt="Stoic Page" src="\screenshots\stoic.page_screenshot.png" />
		</div>
  	<div class="title">
	 	 <h2>
		<code>{project.name}</code> is a {project.language} project
		</h2>
	  </div>
  	<div class="info">
	  <p>
		<i>Language:</i> {project.language} <br />
		<i>Size:</i> {project.size} KB <br />
		<i>Last commit:</i> {new Date(project.updated_at).toDateString()} <br />
		</div>
 	<div class="links">
	 <h3><a href={project.homepage}>Visit {project.name}</a></h3>
	 <i>Github:</i> <a href={project.svn_url}>{project.name}</a> <br />
	  <i>Dependencies:</i>
		<ul>
			{#each tech as {packageName, id}, i}
			<li target="_blank">
				<a href="https://www.npmjs.com/package/{id}">
					{packageName}
				</a>
			</li>
			{/each}
		</ul>
	 </div>	
</div>
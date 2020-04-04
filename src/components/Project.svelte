<script>
	export let name;
	export let tech;
	export let type;
	export let website;
	export let github;
</script>

	<h2>
		<code>{name}</code> is a {type} project
	</h2>
	Tech used:
	<ul>
		{#each tech as {packageName, id}, i}
		<li target="_blank">
			<a href="https://www.npmjs.com/package/{id}">
				{packageName}
			</a>
		</li>
		{/each}
	</ul>

	<a href={website}>Click Here</a> to see {name}
	<br />
	<a href= 'https://github.com/TomFrink/{github}'>Click Here</a> to see {name}'s code on GitHub

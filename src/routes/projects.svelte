<script>
	import Project from '../components/Project.svelte';

	const projectdetails = {
		name: 'Stoic Page',
		type: 'Vue',
		tech: [
			{packageName: 'Vue.js',id:'vue'},
			{packageName: 'Google Firebase', id:'firebase'},
			{packageName: 'Vuefire', id:'vuefire'}
		],
		website: 'https://stoic.page',
		github: 'StoicPage'
  };
</script>

<svelte:head>
  <title>Projects</title>
</svelte:head>

<h1>Projects</h1>

<Project {...projectdetails}/>

<script>
	import { tweened } from 'svelte/motion';

	import Header from './components/Header.svelte';
	import Footer from './components/Footer.svelte';
	import PollList from './components/PollList.svelte';
	import CreatePollForm from './components/CreatePollForm.svelte';
	import Tabs from './shared/Tabs.svelte';

	// tabs
	let tabs = ['Current Polls', 'Add New Poll'];
	let activeTab = 'Add New Poll';

	function tabChange(e) {
		const clickedTab = e.detail;
		activeTab = clickedTab;
	}

	function handleAdd(e) {
		activeTab = 'Current Polls';
	}
</script>

<Header />
<main>
	<Tabs {tabs} {activeTab} on:tabChange={tabChange} />
	{#if activeTab === 'Current Polls'}
		<PollList />
	{:else}
		<CreatePollForm on:add={handleAdd} />
	{/if}
</main>
<Footer />

<style>
	main {
		max-width: 960px;
		margin: 40px auto;
	}
</style>
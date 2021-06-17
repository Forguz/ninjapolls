<script>
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

	let polls = [
		{
			id: 1,
			question: 'Python or JavaScript?',
			answerA: 'Python',
			answerB: 'JavaScript',
			votesA: 9,
			votesB: 15
		}
	]

	function handleAdd(e) {
		const poll = e.detail;
		polls = [poll, ...polls];
		activeTab = 'Current Polls';
	}

	function handleVote(e) {
		const { option, id } = e.detail;

		const copiedPolls = [...polls];
		const upVotedPoll = copiedPolls.find(poll => poll.id === id);

		option === 'a' && upVotedPoll.votesA++;
		option === 'b' && upVotedPoll.votesB++;

		polls = copiedPolls;
	}
</script>

<Header />
<main>
	<Tabs {tabs} {activeTab} on:tabChange={tabChange} />
	{#if activeTab === 'Current Polls'}
		<PollList {polls} on:vote={handleVote} />
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
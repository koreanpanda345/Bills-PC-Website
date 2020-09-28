<template>
  <div class="container">

		<vs-col>
		<CommandNavbar />
		<br>
		<p v-if="$fetchState.pending">Fetching Data...</p>
		<p v-else-if="$fetchState.error">An Error Occured</p>
		<vs-alert warn shadow>
			<template #title>
				Draft Commands
			</template>
			<h2>
				Draft Commands allow you to make a draft plan to either help during the draft process, or help you prep for matches.
			</h2>
		</vs-alert>
		<br>
		<vs-alert border data-aos="fade-left">
			<template #title>
				Making a New Draft Plan
			</template>
			<p>
				Making a new Draft Plan is realy easy to do. just use <a href="#adddraft">b!adddraft</a> command, and follow the embed's instructions.
				<br>
				Example
				<br>
				<br>
				<vs-alert dark solid>
					b!adddraft
				</vs-alert>
			</p>
		</vs-alert>
		<br>
			<vs-alert border data-aos="fade-right">
			<template #title>
				Deleting a Draft plan
			</template>
			<p>
				To delete a Draft Plan you first need to know what the <a href="#draft-id">draft's id</a> that you wish to delete by using <a href="#deletedraft">b!deletedraft</a> command
			</p>
		</vs-alert>
		<br>
			<vs-alert border data-aos="fade-left">
			<template #title>
				Getting A Draft plan
			</template>
			<p>
				To get a draft plan, you need to know what the <a href="#draft-id">draft's id</a> that you want to get. By using the <a href="#viewdraft">b!viewdraft</a> command.
			</p>
		</vs-alert>
		<br>
				<vs-alert border data-aos="fade-right">
			<template #title>
				How to use the Teambuilder command.
			</template>
			<p>
				The Teambuilder command is extremely useful, but can be confusing to use. to use it, you need to use the <a href="#teambuilder"></a> command,
				and the argument you pass is the <a href="#draft-id">draft's id</a> of the draft you want to use. then you will pass the opponents team, by separating the pokemon by new lines.
				Then you will be given 4 reactions, the first on is the team matchup, the second one is your weakness chart, the 3rd is the opponent's weakness chart, then the last one is to close the teambuilder.
			</p>
		</vs-alert>
		<br>
		<vs-alert border id="draft-id" data-aos="fade-left">
			<template #title>
				Draft Ids
			</template>
			Draft Ids is how Bill's PC knows which draft plan you are referring to. Majority of the Draft Commands need the Draft id. You can find the draft plan's id by using the <a href="#draft">b!draft</a> command
		</vs-alert>
		<br>
		<vs-alert warn shadow data-aos="flip-left" data-aos-easing="ease-out-cubic" data-aos-duration="2000">
			<template #title>
				Commands
			</template>
			<h2>
				Below are the commands in this category.
			</h2>
			<br>
			<h2>
				Understanding arguments, {} means it is required, and () means it is optional.
			</h2>
		</vs-alert>
		<br><br>
		<vs-alert
		warn
		border
		data-aos="flip-up"
		v-for="cmd in commands"
		:key="cmd"
		:id="cmd.name">
			<template #title>
				{{cmd.name}}
			</template>
			<h2>Description: {{cmd.description}}</h2>
			<h2>Usage: {{cmd.usage}}</h2>
		</vs-alert>
		<br>
		</vs-col>
  </div>
</template>
<script>
import CommandNavbar from '@/components/CommandNavbar'
export default {
	data: () => ({
		active: 'team',
		commands: {}
	}),
	components: {
		CommandNavbar
	},
	async fetch () {
		this.commands = await fetch('https://bills-pc.codyspratford.repl.co/commands').then(async (res) => {
			const data = await res.json()
			return data.filter(x => x.category === 'Draft')
		})
	}
}
</script>
<style>
</style>

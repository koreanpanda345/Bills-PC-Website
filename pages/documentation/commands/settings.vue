<template>
  <div class="container">

		<vs-col>
		<CommandNavbar />
		<br>
		<p v-if="$fetchState.pending">Fetching Data...</p>
		<p v-else-if="$fetchState.error">An Error Occured</p>
		<vs-alert warn shadow>
			<template #title>
				Settings Commands
			</template>
			<h2>
				Settings command is used to customize Bill's PC to fit how you want it to be in a Server.
			</h2>
		</vs-alert>
		<br>
		<br><br>
		<vs-alert warn border data-aos="flip-up" v-for="cmd in commands" :key="cmd">
			<template #title>
				{{cmd.name}}
			</template>
			<h2>Description: {{cmd.description}}</h2>
			<h2>Aliases: {{cmd.aliases.join(", ")}}</h2>
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
			return data.filter(x => x.category === 'Settings')
		})
	}
}
</script>
<style>
</style>

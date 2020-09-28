<template>
  <div class="container">

		<vs-col>
		<CommandNavbar />
		<br>
		<p v-if="$fetchState.pending">Fetching Data...</p>
		<p v-else-if="$fetchState.error">An Error Occured</p>
		<vs-alert warn shadow>
			<template #title>
				Tool Commands
			</template>
			<h2>
				Team Commands are commands that stores your teams to your very own "PC".
			</h2>
		</vs-alert>
		<br>
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
			return data.filter(x => x.category === 'Tools')
		})
	}
}
</script>
<style>
</style>

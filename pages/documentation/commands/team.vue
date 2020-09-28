<template>
  <div class="container">

		<vs-col>
		<CommandNavbar />
		<br>
		<p v-if="$fetchState.pending">Fetching Data...</p>
		<p v-else-if="$fetchState.error">An Error Occured</p>
		<vs-alert warn shadow>
			<template #title>
				Team Commands
			</template>
			<h2>
				Team Commands are commands that stores your teams to your very own "PC".
			</h2>
		</vs-alert>
		<br>
		<vs-alert border data-aos="fade-left">
			<template #title>
				Adding A Team
			</template>
			<p>
				To add a team to your "PC" you will use the <a href="#addteam">b!addteam</a> command
				You can use a Pokepaste url, or add the team in manually.
				<br>
				Example
				<br>
				<br>
				<vs-alert dark solid>
					b!addteam {pokepaste url}
					<br>
					b!addteam {team name}, {team paste}
				</vs-alert>
			</p>
		</vs-alert>
		<br>
			<vs-alert border data-aos="fade-right">
			<template #title>
				Deleting A Team
			</template>
			<p>
				To delete a team you first need to know what the <a href="#team-id">team's id</a> that you wish to delete by using <a href="#delteam">b!delteam</a> command
			</p>
		</vs-alert>
		<br>
			<vs-alert border data-aos="fade-left">
			<template #title>
				Getting A Team
			</template>
			<p>
				To get a team, you need to know what the <a href="#team-id">team's id</a> that you want to get. By using the <a href="#getteam">b!getteam</a> command.
			</p>
		</vs-alert>
		<br>
				<vs-alert border data-aos="fade-right">
			<template #title>
				Export to PokePaste
			</template>
			<p>
				To Export your team to a pokepaste, you first need to know what the <a href="#team-id">team's id</a> that you wish to export.
				Then you can use either the <a href="#pasteteam">b!pasteteam</a> command or the <a href="#getteam">b!getteam</a> command, and use the export reaction to export it.container.
			</p>
		</vs-alert>
		<br>
		<vs-alert border id="team-id" data-aos="fade-left">
			<template #title>
				Team Ids
			</template>
			Team Ids is how Bill's PC knows which team you are referring to. Majority of the Team Commands need the team id. You can find the team's id by using the <a href="#team">b!team</a> command
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
		<vs-alert danger data-aos="zoom-in" v-if="cmd.disabled === false">
			<h2>This command is disabled as it doesn't work, or is being worked on.</h2>
		</vs-alert>
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
			return data.filter(x => x.category === 'Team')
		})
	}
}
</script>
<style>
</style>

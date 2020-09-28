<template>
  <div class="container">
    <vs-col>
      <p v-if="$fetchState.pending"></p>
        <p v-else-if="$fetchState.error">An Error occured</p>
        <div v-else>
          <vs-alert warn shadow>
            <h1>Bill's PC is on {{stats.stats.servers}} Server</h1>
          </vs-alert>
        </div>
    <vs-row>
      <vs-card type="1">
        <template #title>
          <h2>
            Why Should You Use Bill's PC?
          </h2>
        </template>
        <template #img>
          <img
            src="/Screenshot_1.png"
            alt="screenshot"/>
        </template>
        <template #text>
          Bill's PC isn't like other bots. Bill's PC was design to make your life easier.
          Bill's PC is a Pokemon Showdown Team Storage, that stores your teams into a place called
          the "PC". Not just that, a month after Bill's PC was made, it was being developed to help Draft Players
          by saving their draft plans for them. Then Started to do crazy things with the draft plans, like making a
          prep environment for draft players to build for their draft matches. Bill's PC was design to work with
          Pokemon Showdown, But it learn how to read Smogon's Data, and now it knows everything that Smogon knows.
        </template>
      </vs-card>
	<iframe
	src="https://discordapp.com/widget?id=683919338192764949&theme=dark"
	width="350"
	height="500"
	allowtransparency="true"
	frameborder="0"
	sandbox="allow-popups allow-popups-to-escape-sandbox allow-same-origin allow-scripts"></iframe>
    </vs-row>
    </vs-col>
</div>
</template>

<script>
export default {
      data () {
        return {
            stats: {
                stats: {
                    servers: '',
                    members: '',
                    text: '',
                    voice: '',
                    memberUsage: '',
                    dVersion: '',
                    nVersion: ''
                }
            }
        }
    },
    async fetch () {
        this.stats = await fetch('https://bills-pc.codyspratford.repl.co/stats').then(res => res.json())
    }
}
</script>

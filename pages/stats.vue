<template>
    <div class="container">
        <p v-if="$fetchState.pending">Fetching Stats...</p>
        <p v-else-if="$fetchState.error">An Error occured</p>
        <div v-else>
        <vs-alert warn shadow data-aos="slide-left">
            <template #title>
                Stats
            </template>
            <h2>
            Servers: {{stats.stats.servers}}<br>
            Members: {{stats.stats.members}}<br>
            Uptime: {{stats.stats.uptime}}<br>
            Text Channels: {{stats.stats.text}}<br>
            Voice Channels: {{stats.stats.text}}<br>
            Memory Usage: {{stats.stats.text}}<br>
            Discord Version: {{stats.stats.dVersion}}<br>
            Node Version: {{stats.stats.nVersion}}<br>
            </h2>
        </vs-alert>
        </div>
    </div>
</template>
<script>
// "servers":23,"members":44407,"text":578,"voice":116,"uptime":"2 secs","memoryUsage":"71.29","dVersion":"12.3.1","nVersion":"v12.18.3"
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

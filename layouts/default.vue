<template>
    <div>
        <div>
            <vs-navbar
                center-collapsed
                v-model="active"
                color="dark"
                style="color: white;"
                id="content-desktop"
            >
                <template #left>
                    <img src="/g856.png" alt="logo" style="width: 50px;" />
                </template>
                <template #default>
                    <vs-navbar-item :active="active == 'home'" id="home" to="/">
                        Home
                    </vs-navbar-item>
                    <vs-navbar-item
                        :active="active == 'about'"
                        id="about"
                        to="/about"
                    >
                        About
                    </vs-navbar-item>
                    <vs-navbar-item
                    :active="active == 'stats'"
                    id="stats"
                    to="/stats">
                        Stats
                    </vs-navbar-item>
                    <vs-navbar-group>
                        Docs
                        <template #items>
                            <vs-navbar-item
                                :active="active == 'team'"
                                id="team"
                                to="/documentation/commands/team"
                            >
                                Team Commands
                            </vs-navbar-item>
                            <vs-navbar-item
                                :active="active == 'draft'"
                                id="draft"
                                to="/documentation/commands/draft"
                            >
                                Draft Commands
                            </vs-navbar-item>
                            <vs-navbar-item
                                :active="active == 'tools'"
                                id="tools"
                                to="/documentation/commands/tools"
                            >
                                Tools Commands
                            </vs-navbar-item>
                            <vs-navbar-item
                                :active="active == 'settings'"
                                id="settings"
                                to="/documentation/commands/settings"
                            >
                                Settings Commands
                            </vs-navbar-item>
                            <vs-navbar-item
                                :active="active == 'other'"
                                id="other"
                                to="/documentation/commands/other"
                            >
                                Other Commands
                            </vs-navbar-item>
                        </template>
                    </vs-navbar-group>
					<vs-navbar-group>
						Partners
						<template #items>
							<vs-navbar-item
							:active="active == 'porygon-bot'"
							id="porygon-bot"
							to="/partners/porygon-bot">
								Porygon Bot
							</vs-navbar-item>
							<vs-navbar-item
							:active="active == 'igl-pokefinium'"
							id="igl-pokefinium"
							to="/partners/igl-pokefinium">
								IGL Pokefinium
							</vs-navbar-item>
                            <vs-navbar-item
							:active="active == 'lcd'"
							id="lcd"
							to="/partners/league-colosseum-draft">
								League Colosseum Draft
							</vs-navbar-item>
						</template>
					</vs-navbar-group>
                    <vs-navbar-item
                    :active="active == 'hallOfFame'"
                    id="hallOfFame"
                    to="/hall-of-fame">
                    Hall Of Fame
                    </vs-navbar-item>
                </template>
            </vs-navbar>
<div class="hidden" id="content-mobile">
      <vs-navbar shadow square center-collapsed v-model="active" color="dark">
          <template #left>
          <vs-button warn border @click="activeSidebar = !activeSidebar" flat icon>
            ☰
          </vs-button>
          </template>
      </vs-navbar>
      <vs-sidebar
        absolute
        v-model="active"
        :open.sync="activeSidebar"
        background="dark"
        textWhite
        >
        <template #logo>
        <img src="/g856.png" alt="logo" style="width: 50px;" />
        </template>
        <vs-sidebar-item id="home" to="/">
          Home
        </vs-sidebar-item>
        <vs-sidebar-item id="about" to="/about">
          About
        </vs-sidebar-item>
        <vs-sidebar-item id="stats" to="/stats">
          Stats
        </vs-sidebar-item>
        <vs-sidebar-group>
            <template #header>
                <vs-sidebar-item arrow>
                    Docs
                </vs-sidebar-item>
            </template>
            <vs-sidebar-item id="team" to="/documentation/commands/team">
                Team Commands
            </vs-sidebar-item>
            <vs-sidebar-item id="draft" to="/documentation/commands/draft">
                Draft Commands
            </vs-sidebar-item>
            <vs-sidebar-item id="tools" to="/documentation/commands/tools">
                Tools Commands
            </vs-sidebar-item>
            <vs-sidebar-item id="settings" to="/documentation/commands/settings">
                Settings Commands
            </vs-sidebar-item>
            <vs-sidebar-item id="other" to="/documentation/commands/other">
                Other Commands
            </vs-sidebar-item>
        </vs-sidebar-group>
        <vs-sidebar-group>
            <template #header>
                <vs-sidebar-item arrow>
                    Partners
                </vs-sidebar-item>
            </template>
            <vs-sidebar-item id="porygonbot" to="/partners/porygon-bot">
                Porygon Bot
            </vs-sidebar-item>
            <vs-sidebar-item id="igl-pokefinum" to="/partners/igl-pokefinium">
                IGL Pokefinium
            </vs-sidebar-item>
            <vs-sidebar-item id="lcd" to="/partners/league-colosseum-draft">
                League Colosseum Draft
            </vs-sidebar-item>
        </vs-sidebar-group>
        <vs-sidebar-item id="hallOfFame" to="/hall-of-fame">
            Hall Of Fame
        </vs-sidebar-item>
      </vs-sidebar>
    </div>
        </div>
        <Nuxt />
        <Footer />
    </div>
</template>
<script>
import Footer from '@/components/Footer'
export default {
name: 'default',
data: () => ({
    active: 'Home',
    activeSidebar: false
}),
components: {
    Footer
}
}
</script>
<style>
html {
    font-family: "Source Sans Pro", -apple-system, BlinkMacSystemFont,
        "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
}
*,
*::before,
*::after {
    box-sizing: border-box;
    margin: 0;
}

.button--green {
    display: inline-block;
    border-radius: 4px;
    border: 1px solid #3b8070;
    color: #3b8070;
    text-decoration: none;
    padding: 10px 30px;
}

.button--green:hover {
    color: #fff;
    background-color: #3b8070;
}

.button--grey {
    display: inline-block;
    border-radius: 4px;
    border: 1px solid #35495e;
    color: #35495e;
    text-decoration: none;
    padding: 10px 30px;
    margin-left: 15px;
}

.button--grey:hover {
    color: #fff;
    background-color: #35495e;
}
</style>

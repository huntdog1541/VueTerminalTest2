<template>
    <div class="prompt" v-show="active">
        <span><span class="username">{{ username }}</span> <span class="white">@</span> <span class="location">{{ location }}</span>:<span class="directory">{{ directory }}></span> </span>
        <input id="inputBox" v-model="command"
               v-on:keyup="typeCommand" v-on:keyup.enter="storeCommand">
        <div id="history"><p>{{ command }}</p></div>
    </div>
</template>

<script>
    import { store } from '../store.js'

    class commands {

        constructor(literal)
        {
            this.prompt = promptUsername + "@" +  promptLocation + promptDirectory;
            this.literal = literal;
        }

        setResponse(response){
            this.response = response;
        }

        setTimePullRequest(timePullRequest) {
            this.timePullRequest = timePullRequest;
        }


    }

    export default {
        name: "prompt",

        props: ['active'],
        store,

        data() {
            return {
                command: '',
                history: [],
                testVar: '',
            }
        },
        computed: {
            username() {
                return this.$store.state.username;
            },
            location() {
                return this.$store.state.location;
            },
            directory() {
                return this.$store.state.directory;
            }
        },

        methods: {
            typeCommand(command) {

            },
            storeCommand() {
                var cmds = new commands(this.command);
                this.history.push(cmds);
            }
        }
    }
</script>

<style scoped>

    .username {
        color: #d08770;
    }

    .location {
        color: #bf616a;
    }

    .directory {
        color: #96b5b4;
    }


</style>
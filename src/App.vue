<template>
    <div id="app">
        <div ref="console" class="console">
            <span class="italic">Type 'help' for more information.</span>
            <div class="logs">
                <CommandInput :command="log.command" :result="log.result" v-for="(log, i) in logs" :key="i" />
            </div>
            <CommandInput :func="executeCommand" main />
        </div>
    </div>
</template>

<script>
import CommandInput from "@/components/CommandInput.vue";

export default {
    name: "App",
    components: { CommandInput },
    data() {
        return {
            logs: [],
        };
    },
    methods: {
        createInputCopy() {},
        executeCommand(e) {
            const command = e.target.value.trim();

            if (!command) return;

            switch (command) {
                case "help":
                    {
                        this.logs.push({
                            command,
                            result: [
                                "Try one of these commands:",
                                "help",
                                "about",
                                "social",
                                "clear"
                            ],
                        });
                    }
                    break;
                case "about":
                    {
                        this.logs.push({
                            command,
                            result: [
                                "I do useless things, like this one and I'm homeless.",
                            ],
                        });
                    }
                    break;
                case "social":
                    {
                        this.logs.push({
                            command,
                            result: [
                                "Discord: notsapinho#2975",
                                "Github: github.com/notsapinho",
                            ],
                        });
                    }
                    break;
                case "clear":
                    {
                        this.logs = [];
                    }
                    break;
                default:
                    {
                        this.logs.push({
                            command,
                            result: [
                                `'${command}' is not recognized as an internal command or external command.`,
                            ],
                        });
                    }
                    break;
            }

            e.target.value = "";
        },
    },
};
</script>

<style>
html,
body,
#app {
    font-family: Consolas;
    background-color: #282828;
    color: #66ff66;
    overflow: hidden;
}

*:focus {
    outline: none;
}

.bold {
    font-weight: bold;
}

.italic {
    font-style: italic;
}

.console {
    margin: 1.2rem;
    display: flex;
    flex-direction: column;
}

.logs {
    display: flex;
    flex-direction: column;
}
</style>

<template>
    <div v-if="main" class="mainInputDiv">
        <span class="bold">$</span> <input type="name" class="mainInput" maxlength="20" @keyup.enter="func" autofocus />
    </div>
    <div v-else class="copiedInputDiv">
        <div class="copiedInputTyper">
            <span class="bold">$</span> <span type="name" class="copiedInput">{{command}}</span>
        </div>
        <div class="resultDiv">
            <span v-for="(res, i) in result" :key="i">{{res}}</span>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        main: Boolean,
        command: String,
        result: Array,
        func: Function,
    },
};
</script>

<style>
.copiedInputDiv {
    display: flex;
    flex-direction: column;
}

.resultDiv {
    color: #ffcc00;
    display: flex;
    flex-direction: column;
}

.copiedInput,
.mainInput {
    font-family: Consolas;
    background: none;
    font-size: 16px;
    border: none !important;
    color: #00ff00;
    pointer-events: default !important;
}
</style>
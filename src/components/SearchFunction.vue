<template>
    <div id="search">
        <input type="text" placeholder="Scrivi qui..."
        v-model="myText"
        >
        <button @click="$emit('inputSearch', myText)">cerca</button>
    </div>
</template>

<script>
export default {
    name: 'SearchFunction',
    data() {
        return {
            myText: "",
        }
    },
}
</script>

<style scoped lang="scss">
    #search {
        input {
            border-width: 1px 0 1px 1px;
            padding: 5px;
            outline: 0;
        }

        button {
            border-width: 1px 1px 1px 1px;
            padding: 5px;
            font-size: 13px;
        }
    }
</style>
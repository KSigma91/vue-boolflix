<template>
    <div id="search">
        <input type="text" placeholder="Scrivi qui..."
        v-model="userText">
        <button @click="$emit('myButton', userText)">cerca</button>
    </div>
</template>

<script>
export default {
    name: 'NavbarHeader',
    data() {
        return {
           userText: ""
        }
    },
    
}
</script>

<style scoped lang="scss">
    #search {
        display: flex;
        justify-content: flex-end;
        align-items: center;
        padding-right: 20px;
        background: #000;
        width: 100%;
        height: 60px;

        input {
            padding: 8px;
            outline: 0;
            border-width: 1px 0 1px 1px;
        }

        button {
            padding: 8px;
            border-width: 1px 1px;
            font-size: 13px;
        }
    }
</style>
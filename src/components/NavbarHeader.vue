<template>
    <div id="search">
        <big>BOOLFLIX</big>
        <div id="interaction">
            <input type="text" placeholder="Scrivi qui..."
            v-model="userText"
            @keyup.enter="$emit('myButton', userText)">
            <button @click="$emit('myButton', userText)">cerca</button>
        </div>
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

<style lang="scss" scoped>
#search {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-right: 20px;
    padding-top: 6px;
    background: #000;
    width: 100%;
    height: 65px;

    big {
        padding: 0 20px;
        font-weight: 600;
        color: red;
        font-size: 1.5rem;
    }

    #interaction {
        display: flex;

        input {
            //display: flex;
            justify-content: flex-end;
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
}
</style>
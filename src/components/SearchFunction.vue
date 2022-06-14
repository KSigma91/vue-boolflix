<template>
   <input type="text" placeholder="cerca"
   v-model="myText" @keyup.enter="$emit('inputSearch', myText)"
   >
   <!-- <button>cerca</button> -->
</template>

<script>
export default {
    name: 'SearchFunction',
    data() {
        return {
            myText: "",
        }
    }
}
</script>

<style scoped lang="scss">
    input {
        padding: 5px;
        outline: 0;
    }
</style>
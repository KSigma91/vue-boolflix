<template>
   <input type="text" placeholder="cerca"
   v-model="mySearch" @keyup.enter="$emit('inputSearch', mySearch)"
   >
   <!-- <button>cerca</button> -->
</template>

<script>
export default {
    name: 'SearchFunction',
    data() {
        return {
            mySearch: "",
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
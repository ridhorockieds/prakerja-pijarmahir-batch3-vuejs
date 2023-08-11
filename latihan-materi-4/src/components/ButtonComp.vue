<template>
    <my-button @click="add">{{text}}</my-button>
</template>

<script>
export default {
    name: "ButtonComp",
    props: {
        type: {
            text: String,
            default: "Button"
        }
    },
    methods: {
        add() {
            this.$emit("add");
        },
        edit() {
            this.$emit("edit");
        },
        delete() {
            this.$emit("delete");
        }
    }
}
</script>

<style scoped>
.btn {
    margin: 0 5px;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
    border: 1px solid #ccc;
}

</style>

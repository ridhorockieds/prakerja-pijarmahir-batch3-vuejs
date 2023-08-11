<template>
    <my-button>{{text}}</my-button>
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
    data() {
        return {
            text: this.type
        };
    },
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

<template>
    <div>
        <h3>this is child tile 3</h3>
        <div>{{ propFromParent }}</div>
        <button @click="emitDataToParent">来吧，给父组件一个数据</button>
    </div>
</template>

<script>
    export default {
        name: "childComponent",
        props: ['propFromParent'],
        mounted() {
        },
        methods: {
            emitDataToParent() {
                this.$emit('propFromChild', {msg: Math.random()})
            }
        }
    }
</script>

<style scoped>

</style>

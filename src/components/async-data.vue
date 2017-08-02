<template>
<div>
    <input type="text" v-model="foo">
    <button @click="emit('update', foo)">asd</button>
</div>
</template>

<script>
    export default {
        props:{
            foo:''
        },
        watch:{
            foo:function (val,old) {
            //    this.$emit('update', val)
            }
        },
        data() {
            return {
                text:'',
            }
        },
        components: {},
        computed: {},
        watch: {},
        created() {

        },
        methods: {}
    }
</script>

<style scoped>

</style>

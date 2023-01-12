<template>
    <update-client-form/>
</template>

<script>

export default {
    data(){
        return {
            clientes:[]
        }
    },
    methods: {
        async UpdateCliente() {
            const req = await fetch('http://localhost:3000/client')
            const data = await req.json()
            this.clientes = data
            console.log(this.clientes, 'CLIENTES')
        }
    },
    mounted() {
        this.UpdateCliente()
    
    }
}
</script>

<style>

</style>
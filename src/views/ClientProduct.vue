<template>
    <div class="container">
        <table class="content-table">
            <thead>
                <tr>
                    <th>Codigo</th>
                    <th>Nome</th>
                    <th>Documento</th>
                    <th>Telefone</th>
                    <th>email</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item, index) in clientes" :key="index">
                    <td>{{ item.id }}</td>
                    <td> {{ item.name }}</td>
                    <td>{{ item.doc }}</td>
                    <td>{{ item.phone }}</td>
                    <td>{{ item.email }}</td>
                </tr>
            </tbody>
        </table>

        <table class="content-table">
            <thead>
                <tr>
                    <th>Codigo</th>
                    <th>Descrição</th>
                    <th>Status</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(item,index) in produtos" :key="index">
                    <td>{{ item.id }}</td>
                    <td>{{ item.nome }}</td>
                    <td v-if="item.ativo == true">Ativo</td>
                    <td v-else>Inativo</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: "clientproduct",
    data() {
        return {
            name: null,
            document: null,
            phone: null,
            email: null,
            clientes: [],
            produtos: []
        }
    },
    methods: {
        async getCliente() {
            const req = await fetch('http://localhost:3000/client')
            const data = await req.json()
            this.clientes = data
            console.log(this.clientes, 'CLIENTES')
        },
        async getProduto() {
            const req = await fetch('http://localhost:3000/product')
            const data = await req.json()
            this.produtos = data
            console.log(this.produtos, 'PRODUTOS')
        }
    },
    mounted() {
        this.getCliente(),
            this.getProduto()
    }
}

</script>

<style lang="sass" scoped>
.container
    display: flex
    justify-content: space-evenly
.content-table 
    border-collapse: collapse
    margin: 25px 0
    font-size: 0.9em
    width: 40%
    border-radius: 5px 5px 0 0
    overflow: hidden
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.15)

.content-table thead tr 
    background-color: #009879
    color: #ffffff
    text-align: left
    font-weight: bold


.content-table th,
.content-table td 
    padding: 12px 15px


.content-table tbody tr 
    border-bottom: 1px solid #dddddd


.content-table tbody tr:nth-of-type(even) 
    background-color: #f3f3f3


.content-table tbody tr:last-of-type 
    border-bottom: 2px solid #009879


.content-table tbody tr.active-row 
    font-weight: bold
    color: #009879


</style>
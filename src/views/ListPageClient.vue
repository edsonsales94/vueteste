<template>
    <div class="container-main">
        <div class="container">
            <table class="content-table ">
                <thead>
                    <tr>
                        <th>Codigo</th>
                        <th>Nome</th>
                        <th>Documento</th>
                        <th>Telefone</th>
                        <th>email</th>
                        <th>Status</th>
                        <th>Acoes</th>
                    </tr>
                </thead>
                <tbody class="scroller">
                    <tr v-for="(item, index) in clientes" :key="index">
                        <td>{{ item.id }}</td>
                        <td> {{ item.name }}</td>
                        <td>{{ item.doc }}</td>
                        <td>{{ item.phone }}</td>
                        <td>{{ item.email }}</td>
                        <td v-if="item.ativo == true">Ativo</td>
                        <td v-else>Inativo</td>
                        <td>
                            <input class="btn" type="submit" value="editar">
                            <input class="btn" type="submit" value="excluir">
                        </td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: "listpageclient",
    data() {
        return {
            clientes: [],
        }
    },
    methods: {
        async getCliente() {
            const req = await fetch('http://localhost:3000/client')
            const data = await req.json()
            this.clientes = data
            console.log(this.clientes, 'CLIENTES')
        }
    },
    mounted() {
        this.getCliente()
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
    width: 80%
    border-radius: 5px 5px 0 0
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.15)
.content-table thead tr 
    background-color: #13141f
    color: #ffffff
    text-align: left
    font-weight: bold

td ,th
    text-align: center !important
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
.btn
    padding: 5px
    margin: 5px
</style>
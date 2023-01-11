<template>
    <div class="container-main">
        <div v-for="(item,index) in listAssociation" :key="index"  class="container">
            <table class="content-table ">
                <thead>
                    <tr>
                        <th>Codigo</th>
                        <th>Nome</th>
                        <th>Documento</th>
                        <th>Telefone</th>
                        <th>email</th>
                        <th>Status</th>
                    </tr>
                </thead>
                <tbody class="scroller">
                    <tr>
                        <td>{{ item.clienteObj.id }}</td>
                        <td>{{ item.clienteObj.name }}</td>
                        <td>{{ item.clienteObj.doc }}</td>
                        <td>{{ item.clienteObj.phone }}</td>
                        <td>{{ item.clienteObj.email }}</td>
                        <td v-if="item.clienteObj.ativo == true">Ativo</td>
                        <td v-else>Inativo</td>
                    </tr>
                    <tr>
                        <th colspan="6">
                            Produtos Associados
                        </th>
                    </tr>
                    <tr>
                        <th colspan="2">Codigo</th>
                        <th colspan="2">Descrição</th>
                        <th colspan="2">Status</th>
                    </tr>
                    <tr v-for="(item, index) in item.arrayproduct" :key="index">
                        <td align="center" colspan="2">{{ item.id }}</td>
                        <td align="center" colspan="2">{{ item.nome }}</td>
                        <td align="center" colspan="2" v-if="item.ativo == true">Ativo</td>
                        <td align="center" colspan="2" v-else>Inativo</td>
                    </tr>
                    
                </tbody>
            </table>
        </div>
    </div>
</template>

<script>
export default {
    name: "listpagetAssosiation",
    data() {
        return {
            client: '',
            product: [],
            listAssociation:[]
        }
    },
    methods: {
        async getCliente() {
            const req = await fetch('http://localhost:3000/association')
            const data = await req.json()
            console.log(data.length)
            this.listAssociation = data
            console.log(this.listAssociation[0].clienteObj.name)
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
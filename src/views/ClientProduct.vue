<template>
    <div class="container-main">
        <div class="container">
            <table class="content-table ">
                <thead>
                    <tr>
                        <th for="radio">Selecine</th>
                        <th>Codigo</th>
                        <th>Nome</th>
                        <th>Documento</th>
                        <th>Telefone</th>
                        <th>email</th>
                        <th>Status</th>
                    </tr>
                </thead>
                <tbody class="scroller">
                    <tr v-for="(item, index) in clientes" :key="index">
                        <td>
                            <input v-if="item.ativo == true" type="radio" name="radio" v-model="clienteObj"
                                :value="item">
                            <input v-else disabled type="radio" name="radio" v-model="clienteObj" :value="item">
                        </td>
                        <td>{{ item.id }}</td>
                        <td> {{ item.name }}</td>
                        <td>{{ item.doc }}</td>
                        <td>{{ item.phone }}</td>
                        <td>{{ item.email }}</td>
                        <td v-if="item.ativo == true">Ativo</td>
                        <td v-else>Inativo</td>
                    </tr>
                </tbody>
            </table>


                <table class="content-table">
                    <thead>
                        <tr>
                            <th>Selecine</th>
                            <th>Codigo</th>
                            <th>Descrição</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="(item, index) in produtos" :key="index">
                            <td>
                                <input v-if="item.ativo == true" type="checkbox" name="radio" v-model="arrayproduct"
                                    :value="item">
                                <input v-else disabled type="checkbox" name="radio" v-model="arrayproduct" :value="item">
                            </td>
                            <td>{{ item.id }}</td>
                            <td>{{ item.nome }}</td>
                            <td v-if="item.ativo == true">Ativo</td>
                            <td v-else>Inativo</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <button @click.prevent="save">Salvar</button>
        <!-- {{ clienteObj }}
    {{ arrayproduct }} -->
    </div>
</template>

<script>
export default {
    name: "clientproduct",
    data() {
        return {
            namecli: null,
            document: null,
            phone: null,
            email: null,
            clientes: [],
            produtos: [],
            clienteObj: null,
            arrayproduct: []
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
        },
        async save() {
            const data = {
                clienteObj: this.clienteObj,
                arrayproduct: this.arrayproduct

            }
            // return console.log(data,'data')
            //     //requisicao post
            const dataJson = JSON.stringify(data)
            const req = await fetch("http://localhost:3000/associar", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: dataJson
            });
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
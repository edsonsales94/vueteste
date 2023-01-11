<template>
    <div class="container-main">
        <div class="container">
            <table class="content-table">
                <thead>
                    <tr>
                        <th>Codigo</th>
                        <th>Descrição</th>
                        <th>Status</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(item, index) in produtos" :key="index">
                        <td>{{ item.id }}</td>
                        <td>{{ item.nome }}</td>
                        <td v-if="item.ativo == true">Ativo</td>
                        <td v-else>Inativo</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <!-- <button @click.prevent="save">Salvar</button> -->
    </div>
</template>

<script>
export default {
    name: "listpageprod",
    data() {
        return {
            produtos: [],
        }
    },
    methods: {
        async getProduto() {
            const req = await fetch('http://localhost:3000/product')
            const data = await req.json()
            this.produtos = data
            console.log(this.produtos, 'PRODUTOS')
        },
    },
    mounted() {
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
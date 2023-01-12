<template>
    <form class="container-form">
        <div class="container-input">
            <label for="name">Nome Cliente: </label>
            <input type="text" v-model="name">
            <!-- {{ this.clientes }} -->
        </div>
        <div class="container-input">
            <label for="document">Documento: </label>
            <input type="text" v-model="document">
        </div>
        <div class="container-input">
            <label for="phone">Telefone: </label>
            <input type="text" v-model="phone">
        </div>
        <div class="container-input">
            <label for="email">E-mail: </label>
            <input type="email" v-model="email">
        </div>
        <div class="container-input">
            <div class="radio">
                <label for="flag" style="margin-right: 15px;">Ativo</label>
                <input class="radio-btn" type="radio" id="flag" name="ativo" v-model="ativo" :value="true">
            </div>
            <div class="radio">
                <label for="flag">Inativo</label>
                <input class="radio-btn" type="radio" id="flag" name="ativo" v-model="ativo" :value="false">
            </div>
        </div>
        <div class="container-input">
            <input class="submit-btn" type="submit" @click.prevent="cadCliente" value="Cadastrar CLiente">
        </div>
        <div class="container-input">
            <!-- <span class="messege">{{ msg }}</span>-->
            <span class="error">{{ error }}</span>
        </div>
    </form>
</template>

<script>
export default {
    name: "client",
    data() {
        return {
            name: '',
            document: '',
            phone: '',
            email: '',
            ativo: false,
            error: '',
            clientes:[]
        }
    },
    methods: {
        clear(campo) {
            this.error = `O campo ${campo} não pode ficar vaziu!!!`
            setInterval(() => this.error = "", 5000)
            return
        },
        async cadCliente(e) {

            if (this.name.trim() == '') {
                return this.clear("nome")
                //  this.error = "O campo nome não pode ficar vaziu!!!"
            }
            if (this.document.trim() == '') {
                return this.error = this.clear("documento")
            }
            if (this.phone.trim() == '') {
                return this.error = this.clear("telefone")
            }
            if (this.email.trim() == '') {
                return this.error = this.clear("email")
            }

            const data = {
                name: this.name,
                doc: this.document,
                phone: this.phone,
                email: this.email,
                ativo: this.ativo
            }
            const dataJson = JSON.stringify(data)
            console.log(dataJson)

            const req = await fetch("http://localhost:3000/client", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: dataJson
            });
            const res = await req.json()
            console.log(res)
            this.msg = "Cadastro realizado com sucesso!"
            // // limpar campos
            this.name = ""
            this.ativo = null
            setInterval(() => this.msg = "", 3000)
            // limpar campos
            this.name = ""
            this.document = ""
            this.phone = ""
            this.email = ""
            this.ativo = null
        },
        async UpdateCliente(a) {
            const req = await fetch('http://localhost:3000/client/')
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

<style lang="sass" scoped>
.container-form 
    max-width: 100%
    margin: 0 auto
    padding: 25px 0
.container-input
    width:80%
    display: flex
    flex-direction: column
    margin-bottom: 20px
.container-input label, .submit-btn
    text-align: center
    margin-left: 19%
    
label
    font-weight: bold
    margin-bottom: 15px
    color: #222
    padding: 5px 10px
    border-left: 4px solid #009879
    font-size: 22px

input,select
    padding: 5px 10px
    width: 60%
.radio
    display: flex
    width: 60%
    margin-bottom: 10px
    justify-content: flex-start
    flex-direction: row

#flag
    width: 10%
    margin: 0
    padding: 0
    
.radio label
    border-left: none
    margin: 0
    padding: 0
.submit-btn
    background-color: #222
    color:#009879
    font-weight: bold
    border: 2px solid #222
    padding: 10px
    font-size: 22px
    margin: 0 auto
    cursor: pointer
    transition: .5s    
.submit-btn:hover 
    background-color: transparent
    color: #222
.messege
    background: green
    width:  60%
    text-align: center
    color: #fff
    font-weight: bold
    font-size: 18px
.error
    background: red
    width:  60%
    text-align: center
    color: #fff
    font-weight: bold
    font-size: 18px


@media (max-width: 600px) 
    .container-input input
        padding: 3px 0
        font-size: 20px


</style>
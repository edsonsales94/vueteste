<template>
    <div class="header">
        <nav class="container-header">
            <a href="/">
                <h2 class="logo">SYSTEM :)</h2>
            </a>
            <div class="menu-item">
                <router-link class="text-nav" to="/product">Produtos</router-link>
                <router-link class="text-nav" to="/client">Clientes</router-link>
                <router-link class="text-nav" to="/cliente_produto">Cli x Prod</router-link>
            </div>
        </nav>
    </div>
</template>

<script>
export default {
    name: 'NavBar',
    data() {
    }
}
</script>


<style lang="sass" scoped>
    div.header
        padding: 50px 0
        background: #13141f
        font: 1.5em sans-serif
    a
        text-decoration: none
        color: #fff
    .text-nav 
        color: #fff
        margin: 10px
        text-decoration: none
        color: white
        font-size: 25px
        text-decoration: none
        transition: 0.5s
    .text-nav:hover 
        color: rgb(88, 96, 139)
        font-weight: bold
        padding: auto   
    .container-header
        width: 100%
        display: flex
        align-content: space-between
        align-items: center
    
    @media (max-width: 600px)
        div.header
            font: 0.8rem sans-serif
        .text-nav 
            font-size: 14px
            
</style>
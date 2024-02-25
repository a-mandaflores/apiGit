<template>

    <div v-if="infos" class="infos">
    <img :receberDados="mostrarDados" :src="infos.avatar_url" alt="">    
    <h1 class="nome">{{ infos.name}}</h1>
    <h1 class="login">{{ infos.login }}</h1>

    <div class="infosapi">
    <h1 class="bio"><span>Bio:</span> {{ infos.bio }}</h1>
    <h1 class="repositorios"><span>Repositorios:</span> {{ infos.public_repos }}</h1>
    <h1 class="seguidores"><span>Seguidores:</span> {{ infos.followers }}</h1>
    <h1 class="seguindo"><span>Seguindo:</span> {{ infos.following }}</h1>
    </div>
</div>
</template>

<script>
import axios from 'axios'



export default{
    data(){
        return{
            infos: null,
        }
    },
    props: {
        loginApi:{
            type: String
        },
        verificar:{
            type: Boolean,
        }
    },
    
    methods:{
        mostrarDados(valor){
            console.log(valor)
            axios.get(`users/${valor}`)
            .then(res => {
                this.infos = res.data
            })
            .catch(error => {
                console.log('Erro na requisição', error)
            })
            .finally(()=>{
                this.$emit('verificado', false)
            })
        },

    },
    watch: {
        verificar(){
            this.mostrarDados(this.loginApi)
        }
    }
    
}
</script>

<style lang="scss" scoped>


.infos{
    width: 100%;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    height: 100%;
    background-color: #333;

    img{
    width: 100px; 
    height: 100px; 
    border-radius: 50%; 
    overflow: hidden; 
    margin: 1rem;
    }
    .nome{
        font-size: .9rem;
        font-weight: 500;
    }
    .login{
        
        font-size: .8rem;
        font-weight: 200;
    }

    .repositorios, .seguidores, .seguindo, .bio{
        font-size: .9rem;
        font-weight: 200;
        margin: 2rem 2rem 0 2rem;

    }
    span{
        font-weight: 600;
    }

    .infosapi{
        margin: 1rem;
    }
}

</style>
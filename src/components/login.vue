<template>
    <div id="login">
        <h1>Login</h1>
        <div>
            <label for="fname">Correo Electrónico:</label><br>
            <input type="text" name="username" v-model="username" placeholder="Ejemplo@mail.com"/>
        </div>
        <div>
            <br>
            <label for="fname">Contraseña:</label><br>
            <input type="password" name="password" v-model="password" placeholder="Mínimo 5 caracteres"/>
        </div>
        <br><button type="button" id="boton" :disabled='!isComplete' v-on:click="sendData()">Login</button>
    </div>
</template>

<script>
    export default {
        name: 'Login',
        data() {
            return {
                //campos usuario
                username: null,
                password: null
            }
        },
        computed: {
            isComplete () {
                //Caracteres incompatibles en un email y estructura requerida para el correo.
                // eslint-disable-next-line
                var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;

                return re.test(this.username) && (this.password.length > 4); //Largo debe ser mayor a 4.
            }
        },
          methods: {
            sendData() {

              alert("Bienvenido " + this.username);
            }
        }
    }
</script>

<style scoped>
    #login {
        width: 500px;
        border: 3px solid #f1f1f1;
        background-color: #FFFFFF;
        margin: auto;
        margin-top: 200px;
        padding: 20px;
    }
    button {
        width: 50%;
        background-color: #4CAF50;
        color: white;
        padding: 14px 20px;
        margin: 8px 0;
        border: none;
        border-radius: 4px;
        cursor: pointer;
    }
    :disabled {
        opacity: 0.6;
        cursor: not-allowed;
    }
    input {
        border: 2px solid gray;
        border-radius: 4px;
    }
    label {
        display: inline-block;
        text-align: left;
    }
</style>
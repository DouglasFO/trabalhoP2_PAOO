<template>
    <v-container>
        <v-row class="text-center">
            <v-col cols="12">
                <h1>Loja de Quadrinhos</h1>
                <v-btn depressed color="primary">
                    Inserir
                </v-btn>            
            </v-col>
        </v-row>
        <v-row class="text-center">
            <v-col cols="12">
                <v-data-table dense :headers="headers" :items="users" item-key="name" class="elevation-1">
                </v-data-table>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
import axios from "axios";
export default {
    name: "UserCrud",
    data: () => ({
            headers: [
                {text: "Nome", value: "name"},
                {text: "Preço", value: "price"},
                {text: "Quantidade", value: "qtde"},
                {text: "Actions", value: "icon"}
            ],
            users: [
                {id: 1, name: "Douglas", location: "Rio de Janeiro"},
                {id: 1, name: "João", location: "Bahia"}
            ],
    }),
    methods: {
        inicializa() {
            axios("http://localhost:3000/users")
            .then((response)=> {
                    this.users = response.data;
            })
            .catch((error)=> console.log(error));
        }
    },
    created() {
        this.inicializa();
    }
};
</script>
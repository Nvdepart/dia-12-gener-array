<template>
    
        <v-row>
          <v-col >
            <h2>Llista de Mascotes</h2>
            <div >
                <v-card class="bgColor pa-5 md-10 mr-2" v-for="mascota in mascotas" :key="mascota.nombre">
                  <v-card-title>{{mascota.nombre}}</v-card-title>
                  <v-card-subtitle>{{mascota.especie}}</v-card-subtitle>
                  <v-card-text>Edad:<strong>{{mascota.edad}} </strong> anys</v-card-text>
                </v-card>
            </div>
          </v-col>
          <v-col><h2>Accions</h2> <br>
            
                <v-btn color="green" @click="OrdenarAZ">Ordenar A-Z</v-btn>
                <v-btn color="green" @click="OrdenarZA">Ordenar Z-A</v-btn>
                <v-btn color="green" @click="Ordenarlg">Ordenar Length</v-btn>
                <v-text-field 
                    type="text" 
                    v-model="nombreFiltro" 
                    @input="filtrarPorNombre()"
                ></v-text-field>
          </v-col>
        </v-row>
   
</template>

<script>
    export default {
        
        data(){
            return {  mascotas:[
                {nombre: "Gato", especie: "Felis catus", edad: 3},
                {nombre: "Perro", especie: "Canis lupus familiaris", edad: 7},
                {nombre: "Hamster", especie: "Mesocricetus auratus", edad: 2},
                {nombre: "Pez", especie: "Carassius auratus", edad: 1},
                {nombre: "Loro", especie: "Psittacidae", edad: 5},
                {nombre: "Conejo", especie: "Oryctolagus cuniculus", edad: 4},
                {nombre: "Tortuga", especie: "Testudines", edad: 10},
                {nombre: "Iguana", especie: "Iguana iguana", edad: 6},
                {nombre: "Rana", especie: "Rana sp.", edad: 1},
                {nombre: "Serpiente", especie: "Serpentes", edad: 3},
                {nombre: "Ratón", especie: "Mus musculus", edad: 2},
                {nombre: "Pájaro", especie: "Aves", edad: 4},
                {nombre: "Cobaya", especie: "Cavia porcellus", edad: 3},
                {nombre: "Erizo", especie: "Erinaceidae", edad: 4},
                {nombre: "Ardilla", especie: "Sciurus sp.", edad: 2}
            ],
            mascotasFiltradas: [],
            nombreFiltro:'',
        };
           

        },
        methods:{
            OrdenarAZ(){
                this.mascotas.sort(function(a, b) {
                    if (a.nombre < b.nombre) {
                        return -1;
                    }
                    if (a.nombre > b.nombre) {
                        return 1;
                    }
                    return 0;
                   
                    console.log(this.mascotas);
                })
            },
            OrdenarZA(){
                    /*this.mascotas.sort((a, b) => b.nombre - a.nombre);
                    console.log(this.mascotas);*/
                this.mascotas.sort(function(a, b) {
                    if (a.nombre > b.nombre) {
                        return -1;
                    }
                    if (a.nombre < b.nombre) {
                        return 1;
                    }
                    return 0;
                   
                    console.log(this.mascotas);
                })
            },
            Ordenarlg(){
                    /*this.mascotas.sort((a, b) => b.nombre - a.nombre);
                    console.log(this.mascotas);*/
                this.mascotas.sort(function(a, b) {
                    if (a.nombre.length < b.nombre.length) {
                        return -1;
                    }
                    if (a.nombre.length > b.nombre.length) {
                        return 1;
                    }
                    return 0;
                   
                    console.log(this.mascotas);
                })
            },
            filtrarPorNombre(nombreFiltro) {
                    this.mascotasFiltradas = this.mascotas.filter(mascota => 
                    mascota.nombre.toLowerCase().includes(this.nombreFiltro.toLowerCase()));
                    console.log(nombreFiltro);
                }
        },
        computed: {
            mascotasOrdenadas() {
                    return this.mascotas.sort((a, b) => {
                        if (a.nombre < b.nombre) return -1;
                        if (a.nombre > b.nombre) return 1;
                        return 0;
                    });
                },
            mascotasFiltradas() {
                    return this.mascotas.filter(mascota => mascota.nombre.toLowerCase().includes(this.filtro.toLowerCase()));
                    }
                },
            
        created(){
                
            this.mascotasFiltradas = this.mascotas
            }
        }

</script>

<style scoped>
.bgColor{
    background-color: rgba(77, 230, 39, 0.5);
    border-radius: 20%;
    
}
</style>
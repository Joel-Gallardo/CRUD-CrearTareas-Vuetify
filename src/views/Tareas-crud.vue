<template>
    <v-container>
        <v-row>
            <v-col>
                <v-card class="mb-3" v-for="(item, index) in listaTareas" :key="index">
                    <v-card-text>
                        <v-chip class="ma-2 ml-0" color="pink" label text-color="white">
                            <v-icon left>
                                mdi-label
                            </v-icon>
                            {{item.titulo}}
                        </v-chip>
                        <p>
                            {{item.descripcion}}
                        </p>
                        <v-btn color="warning" @click="editar(index)" class="mr-3">Editar</v-btn>
                        <v-btn color="error" @click="eliminarTarea(item.id)">Eliminar</v-btn>
                    </v-card-text>
                </v-card>
            </v-col>

            <v-col v-if="formAgregar">
                <v-card class="pa-5">
                    <v-form @submit.prevent="agregarTarea">
                        <v-text-field label="Titulo de la Tarea" v-model="titulo"></v-text-field>
                        <v-textarea label="Descripción de mi tarea" v-model="descripcion"></v-textarea>
                        <v-alert type="error" v-model="alertaCamposVacios">
                            {{msj}}
                        </v-alert>
                        <v-snackbar :timeout="timeout" v-model="alertaTareaAgregada">
                            {{msj}}
                        </v-snackbar>
                        <v-btn block color="success" type="submit">Agregar Tarea</v-btn>
                    </v-form>
                </v-card>
            </v-col>

            <v-col v-if="!formAgregar">
                <v-card class="pa-5">
                    <v-form @submit.prevent="editarTarea()">
                        <v-text-field label="Titulo de la Tarea" v-model="titulo"></v-text-field>
                        <v-textarea label="Descripción de mi tarea" v-model="descripcion"></v-textarea>
                        <v-alert type="error" v-model="alertaCamposVacios">
                            {{msj}}
                        </v-alert>
                        <v-snackbar :timeout="timeout" v-model="alertaTareaAgregada">
                            {{msj}}
                        </v-snackbar>
                        <v-btn block color="warning" type="submit">Editar Tarea</v-btn>
                    </v-form>
                </v-card>
            </v-col>

        </v-row>
    </v-container>
</template>

<script>
    export default {
        data() {
            return {
                listaTareas: [
                    // {
                    //     id: 1,
                    //     titulo: 'Titulo tarea #1',
                    //     descripcion: '1 esto es una descripcion de la tarea a realizar por favor especifique todo es este apartado'
                    // },
                    // {
                    //     id: 2,
                    //     titulo: 'Titulo tarea #2',
                    //     descripcion: '2 esto es una descripcion de la tarea a realizar por favor especifique todo es este apartado'
                    // }
                ],
                titulo: '',
                descripcion: '',
                alertaCamposVacios: false,
                alertaTareaAgregada: false,
                timeout: 3000,
                msj: '',
                formAgregar: true,
                indexTarea: ''
            }
        },
        methods: {
            agregarTarea() {
                if (this.titulo === '' || this.descripcion === '') {
                    this.alertaCamposVacios = true;
                    this.msj = 'Llena Todos los Campos'
                } else {
                    //aggrgando al arreglo la tarea creada
                    this.alertaCamposVacios = false;
                    this.listaTareas.push({
                        id: Date.now(), //añade como id la hora exacta que se agrego la tarea
                        titulo: this.titulo,
                        descripcion: this.descripcion
                    });
                    //borrado de variables
                    this.titulo = '';
                    this.descripcion = '';
                    this.alertaTareaAgregada = true;
                    this.msj = 'Tarea Agregada Exitosamente!';
                }
            },
            eliminarTarea(id) {
                this.listaTareas = this.listaTareas.filter(e => e.id != id)
            },
            editar(index) {
                this.formAgregar = false;
                this.titulo = this.listaTareas[index].titulo;
                this.descripcion = this.listaTareas[index].descripcion;
                this.indexTarea = index;

            },
            editarTarea() {
                if (this.titulo === '' || this.descripcion === '') {
                    this.alertaCamposVacios = true;
                    this.msj = 'Llena Todos los Campos'
                } else {
                    //aggrgando al arreglo la tarea creada
                    this.alertaCamposVacios = false;
                    this.listaTareas[this.indexTarea].titulo = this.titulo;
                    this.listaTareas[this.indexTarea].descripcion = this.descripcion;
                    //borrado de variables
                    this.titulo = '';
                    this.descripcion = '';
                    this.alertaTareaAgregada = true;
                    this.msj = 'Tarea Editada Exitosamente!';
                    this.formAgregar = true;
                }

            }
        }
    }
</script>
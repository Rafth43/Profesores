<script lang="ts" setup>
import { ref, Ref } from 'vue';

    interface IProfesor{
        Nombres: string,
        Apellidos: string,
        Cedula: string,
        materias: Array<string>,
        documentacion: boolean
    }

    let profesor:Ref<IProfesor> = ref({
        Nombres: '',
        Apellidos: '',
        Cedula: '',
        materias: [],
        documentacion: false,
    })

    let profesores:Ref<Array<IProfesor>> = ref([]);

    let materia:Ref<string> = ref('')

    const handleMateria = () => {
        profesor.value.materias.push(materia.value);
        materia.value = "";
    }
    const sustractMateria = (a) => {
        profesor.value.materias.splice(a, 1);
    }


</script>

<template>
    <div style="display: flex;">
        <div class="card">
            <h1>Información de profesor</h1>
            <div class="card_i">
                <label for="">Nombres del profesor:</label>
                <input type="text" v-model="profesor.Nombres">
            </div>
            <div class="card_i">
                <label for="">apellidos del profesor:</label>
                <input type="text" v-model="profesor.Apellidos">
            </div>
            <div class="card_i">
                <label for="">Cedula del profesor:</label>
                <input type="text" v-model="profesor.Cedula">
            </div>
            <div class="card_i">
                <label for="">Clases a impartir:</label>
                <input type="text" v-model="materia">
            </div>
            <div class="agregar">
                <button @click="handleMateria">Agregar</button>
                
            </div>
            <div class="materias">
                <div class="listado" v-for="(item, index) in profesor.materias" :key="index"><a class="btn_d" @click="sustractMateria(index)">x</a><span>{{ item }}</span></div>
            </div>
            <div class="card_i">
                <span for="" class="mensaje">Esta deacuerdo con la información suministrada</span>
                <input type="checkbox" v-model="profesor.documentacion">
            </div>
    
            <button type="button" style="width: 90%;">Enviar</button>
        </div>
        <div class="card">
            <h1>Listado de profesores</h1>
            <div style="display: flex;">
                <div class="card_p">
                    hola
                </div>
                <div class="card_p">
                    hola
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    margin: auto;
    width: 30%;
    height: 50%;
    box-shadow: 0px 10px 15px -3px rgba(0,0,0,0.1);
    border-radius: 10px;
}

.card_i {
    display: flex;
    flex-direction: column;
}

.agregar{
    margin-right: 20px;
    display: flex;
    justify-content: end;
}
.mensaje{
    display: flex;
    justify-content: center;
    font-size: small;
}

.materias{

    width: 100%;
    display: flex;
    justify-content: space-evenly;

}

.listado {
    background-color: rgb(241, 239, 235);
    width: 19%;
    height: 50px;
    overflow: auto;
    white-space: normal;
    margin-bottom: 10px;
    box-shadow: 0px 4px 5px 1px rgba(0,0,0,0.1);
    border-radius: 9px;
}

.card_p{
    width: 50%;
    height: 50px;
    background-color: aliceblue;
    justify-content: space-between;
    border-radius: 5px;
    margin: 10px;
}

.btn_d{
    display: flex;
    justify-content: end;
    margin-right: 10px;
    cursor: pointer;
    color: #c20f0f;
    font-weight: 500;
}

input {
    width: 93%;
    height: 28px;
    margin: 2px 10px 10px;
    border: 1px solid rgba(73, 151, 253, 0.479);
    border-radius: 5px;
}

label {
    display: flex;
    margin-left:10px ;
    font-size: medium;
}

button{
    background-color: rgba(73, 151, 253, 0.479);
    border: none;
    height: 35px;
    width: 70px;
    border-radius: 5px;
    margin-bottom: 15px;
    color: aliceblue;
    font-size: small;
    font-weight: 600;
    cursor:pointer;
}

span{
    margin: auto;
    display: flex;
    justify-content: center;
}

button:hover{
    background-color:rgb(226, 234, 240) ;
    color: rgba(73, 151, 253, 0.479);
    
}

</style>
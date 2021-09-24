<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Triaje</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">REGISTRO DE TRIAJE</ion-title>
        </ion-toolbar>
      </ion-header>

      <ion-grid>
        <ion-list lines="full" class="ion-no-margin">
          <ion-row>
            <ion-item>
              <h3>SELECCIÓN DE PACIENTE</h3>
            </ion-item>

            <ion-item>
              <ion-select
                interface="action-sheet"
                placeholder="Seleccione uno"
                v-model="pacienteSeleccionado"                
                @change="actualizarPacienteSeleccionado"
              >
                <ion-select-option
                  v-for="(item, index) in pacientes"
                  :key="index"
                  :value="item"
                  >{{ item.nombresCompletos }}</ion-select-option
                >
              </ion-select>
            </ion-item>
          </ion-row>
        </ion-list>
        </ion-grid>
        <ion-grid>        
          <ion-list lines="full" class="ion-no-margin">
            <ion-row>
            <ion-item>
              <h3>REGISTRO DE TRIAJE</h3>
            </ion-item>
            <ion-item>
              <ion-label position="stacked">Paciente atendido</ion-label>
              <ion-input v-model="pacienteSeleccionado.nombresCompletos" disabled></ion-input>
            </ion-item>
            <ion-item>
              <ion-label position="stacked">Fecha de atención</ion-label>
              <ion-input v-model="triaje.fecha" type="date"> </ion-input>
            </ion-item>
            <ion-item>
              <ion-label position="stacked">Peso (Kg.)</ion-label>
              <ion-input
                v-model="triaje.peso"
                type="number"
                placeholder="ejm: 60"
              >
              </ion-input>
            </ion-item>
            <ion-item>
              <ion-label position="stacked">Temperatura (°C)</ion-label>
              <ion-input
                v-model="triaje.temperatura"
                type="number"
                placeholder="ejm: 36"
              >
              </ion-input>
            </ion-item>
            <ion-item>
              <ion-label position="stacked">Presion (mm Hg)</ion-label>
              <ion-input
                v-model="triaje.presion"
                type="number"
                placeholder="ejm: 120"
              >
              </ion-input>
            </ion-item>
            <ion-item>
              <ion-label position="stacked">Nivel de saturación (%) </ion-label>
              <ion-input
                v-model="triaje.nivelSaturacion"
                type="number"
                placeholder="ejm: 95"
              >
              </ion-input>
            </ion-item>
            </ion-row>
          </ion-list>        
      </ion-grid>
      <ion-button
        color="success"
        size="small"
        expand="block"
        @click="agregarConsulta"
        >Registrar triaje</ion-button
      >
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
  IonList,
  IonItem,
  IonInput,
  IonButton,
  IonGrid,
  IonRow,
  IonSelect,
  IonSelectOption,
} from "@ionic/vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "Tab1",
  data() {
    return {
      pacienteSeleccionado: {
          id: "",
          nombresCompletos: "",
          fechaNacimiento: "",
          estatura: null,
          direccion: "",
          ubicacion: "",
      },
      pacientes: [
        {
          id: "asdf",
          nombresCompletos: "Maria Casas",
          fechaNacimiento: "",
          estatura: 1.6,
          direccion: "An siempre viva",
          ubicacion: "Calle los álamos 234",
        },
        {
          id: "hjuy",
          nombresCompletos: "Juan Pérez",
          fechaNacimiento: "",
          estatura: 1.6,
          direccion: "An siempre viva",
          ubicacion: "Calle los álamos 234",
        },
      ],
      triaje: {
        idPaciente: "",
        nombresCompletos: "",
        peso: 60.5, // Kg
        temperatura: 37, //°C
        presion: 120, //  en mm Hg
        nivelSaturacion: 95, // porcentual
        fecha: "",
      },
    };
  },
  created(){
    this.listarPacientes()

  },
  methods: {
    agregarConsulta() {
      console.log("Agregando consulta");
      this.actualizarPacienteSeleccionado();
      console.log(this.triaje);
      // AQUI CODIGO PARA GUARDAR EN FIREBASE
    },
    listarPacientes() {
      // AQUI CODIGO PARA RECUPERAR LOS PACIENTES REGISTRADOS EN FIREBASE
      //this.pacientes =  DATAA; // aqui cambiar por la lista de registros recuperados
      console.log(this.pacientes);
    },
    actualizarPacienteSeleccionado(){
      console.log("entro");
      this.triaje.idPaciente = this.pacienteSeleccionado.id;
      this.triaje.nombresCompletos = this.pacienteSeleccionado.nombresCompletos;
      console.log(this.triaje);

    }
  },

  components: {
    IonHeader,
    IonToolbar,
    IonTitle,
    IonContent,
    IonPage,
    IonList,
    IonItem,
    IonInput,
    IonButton,
    IonGrid,
    IonRow,
    IonSelect,
    IonSelectOption,
  },
});
</script>
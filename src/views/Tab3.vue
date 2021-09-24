<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Atenciones</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">REGISTRO DE ATENCIONES</ion-title>
        </ion-toolbar>
      </ion-header>
     
        <ion-grid>
              <ion-list lines="full" class="ion-no-margin">
                 <ion-row >  
                 <ion-item>
                   <h3> HISTORIAL DE ATENCIONES </h3>
                </ion-item> 
                <ion-row>
                <div v-for="(item, id) in triajes" v-bind:key="id" >
                <ion-card>
                  <ion-card-header>
                    <ion-card-subtitle>{{item.fecha}}</ion-card-subtitle>
                    <ion-card-title>{{item.nombresCompletos}}</ion-card-title>

                  </ion-card-header>
                  <ion-card-content>
                   Peso: {{item.peso}} Kg,  Temperatura: {{item.temperatura}} °C, Presión: {{item.presion}} mm Hg,  Nivel de saturación: {{item.nivelSaturacion}} %
                 
                 </ion-card-content>
                </ion-card>
                </div>
                </ion-row>
                </ion-row>
              </ion-list>          
        </ion-grid>
      
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, 
IonList, IonItem,  IonGrid, IonRow  } from '@ionic/vue';
import { defineComponent } from 'vue';


export default defineComponent(  {
  name: 'Tab1',
  data () {
      return {
        triajes: [
          {
        id:"otroid",
        idPaciente: "hjuy",
        nombresCompletos: "Juan Pérez",
        peso: 60.5, // Kg
        temperatura: 37, //°C
        presion: 120, //  en mm Hg
        nivelSaturacion: 95, // porcentual
        fecha: "2021-09-24",
      },
      {
        id:"otroid2",
        idPaciente: "asdf",
        nombresCompletos: "Maria Casas",
        peso: 60.5, // Kg
        temperatura: 37, //°C
        presion: 120, //  en mm Hg
        nivelSaturacion: 95, // porcentual
        fecha: "2021-09-24",
      }
        ],

      }
  },
  created(){
    this.listarTriajes()

  },
  methods:{
    listarTriajes(){
      console.log("listando triajes");
      console.log(this.triajes);
      // AQUI CODIGO PARA RECUPERAR LA ISTA DE TRIAJES DE FIREBASE
    }

  },
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage,
  IonList, IonItem, IonGrid, IonRow  }
});
</script>
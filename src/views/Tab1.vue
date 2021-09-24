<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Paciente</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">INGRESO PACIENTE</ion-title>
        </ion-toolbar>
      </ion-header>
     
        <ion-grid>
                     
              
              <ion-list lines="full" class="ion-no-margin">
                 <ion-row >  
                 <ion-item>
                   <h3> REGISTRO DE PACIENTE </h3>
                </ion-item> 
                <ion-item>
                  <ion-label position="stacked">Nombres completos</ion-label>
                  <ion-input v-model="paciente.nombresCompletos" value="nombres" placeholder="nombres completos" > </ion-input>
                </ion-item>  
                 <ion-item>
                  <ion-label position="stacked">Fecha</ion-label>
                  <ion-input v-model="paciente.fechaNacimiento" type="date" > </ion-input>
                </ion-item> 
                <ion-item>
                  <ion-label position="stacked">Estatura</ion-label>
                  <ion-input v-model="paciente.estatura" type="number" >  </ion-input>
                </ion-item>  
                <ion-item>
                  <ion-label position="stacked">Dirección</ion-label>
                  <ion-input v-model="paciente.direccion" type="text" > </ion-input>
                </ion-item> 
                <ion-item>
                  <ion-label position="stacked">Ubicación</ion-label>
                  <ion-input v-model="paciente.ubicacion"  >  </ion-input>
                </ion-item> 
                </ion-row>
              </ion-list>
        
        <ion-row>
          <div>
             -- MAPA -- 
            </div>  
      </ion-row>
         
          
        </ion-grid>
  <ion-button color="success" size="small" expand="block" @click="agregarPaciente">Registrar pacientes</ion-button>
    
    
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonPage, IonHeader, IonToolbar, IonTitle, IonContent, 
IonList, IonItem, IonInput,  IonButton, IonGrid, IonRow  } from '@ionic/vue';
import { defineComponent } from 'vue';


export default defineComponent(  {
  name: 'Tab1',
  data () {
      return {
        paciente:{
          nombresCompletos: "Juan Pérez",
          fechaNacimiento : "",
          estatura: 1.60,
          direccion:"An siempre viva",
          ubicacion:"Calle los álamos 234",
        }

      }
  },
  methods:{
    agregarPaciente(){
      console.log("Agregando paciente");
      console.log(this.paciente);
      // AQUI CODIGO PARA GUARDAR EN FIREBASE
    }

  },
  components: { IonHeader, IonToolbar, IonTitle, IonContent, IonPage,
  IonList, IonItem, IonInput, IonButton, IonGrid, IonRow  }
});
</script>
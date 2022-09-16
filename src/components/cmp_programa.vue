<template>
    <v-container fluid>
        <v-layout>
            <v-flex xs4>
                <v-select
                    v-model="cod_prg"
                    :items=ds_prog
                    item-text="programa"
                    item-value="cod_programa"
                    label="Seleccione un programa"
                    outlined
                    @change="get_prog_metas(), kit_por_programa()"
                  >
                  </v-select>
            
                </v-flex>
        
        </v-layout>
      <v-layout class="elevation-1 pa-2">
      <v-flex xs3 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto "
        color="purple darken-4"
        dark
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-cash-multiple
          </v-icon>
          <span class="text-h6 font-weight-bold">PIA</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Presupuesto Institucional de Apertura
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-right">
          S/. {{ parseFloat(this.ds_tot[0].pia).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}
        </v-card-text>


        </v-card>
      </v-flex>


      <v-flex xs3 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto"
        color="blue darken-2"
        dark
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-cash-multiple
          </v-icon>
          <span class="text-h6 font-weight-bold">PIM</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Presupuesto Institucional Modificado
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-right">
          S/. {{ parseFloat(this.ds_tot[0].pim).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}
        </v-card-text>


        </v-card>
      </v-flex>

      <v-flex xs3 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto"
        color="teal darken-2"
        dark
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-cash-multiple
          </v-icon>
          <span class="text-h6 font-weight-bold">CERTIFICADO</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Monto Certificado
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-right">
          S/. {{ parseFloat(this.ds_tot[0].certif).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}
        </v-card-text>


        </v-card>
      </v-flex>

      <v-flex xs3 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto"
        color="lime darken-4"
        dark
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-cash-multiple
          </v-icon>
          <span class="text-h6 font-weight-bold">DEVENGADO</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Monto Devengado
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-right">
          S/. {{ parseFloat(this.ds_tot[0].devengado).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}
        </v-card-text>


        </v-card>
      </v-flex>

      <v-flex xs3 class="ma-0 elevation-10">
        <v-card
        class="mx-auto"
        color="deep-orange darken-4"
        dark
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-cash-multiple
          </v-icon>
          <span class="text-h6 font-weight-bold">SALDO</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Saldo Presupuestal
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-right">
          S/. {{ parseFloat(this.ds_tot[0].saldo).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}
        </v-card-text>


        </v-card>
      </v-flex>
    </v-layout>


    <v-layout class="elevation-1 pa-2">
      <v-flex xs4 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto "
        color="indigo darken-3"
        dark
        height="500"
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-chart-pie
          </v-icon>
          <span class="text-h6 font-weight-bold">Porcentaje de Ejecución Total</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Devengado / PIM
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-center">
          <v-progress-circular
            show-value
            :rotate="270"
            :size="400"
            :width="90"
            :thickness="0.4"
            :value="this.ds_tot[0].ejec"
            color="cyan accent-1"
          >
            {{ parseFloat(this.ds_tot[0].ejec).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} %
          </v-progress-circular>
        </v-card-text>
        </v-card>
      </v-flex>


      <v-flex xs4 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto"
        color="blue darken-2"
        dark
        height="500"
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-chart-pie
          </v-icon>
          <span class="text-h6 font-weight-bold">% de Ejecución por fuente RO</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Ejecución Recursos Ordinarios
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-center">
          <v-progress-circular
            show-value
            :rotate="270"
            :size="290"
            :width="40"
            :thickness="0.4"
            :value="this.ro_eje"
            color="cyan accent-1"
          >
            {{ parseFloat(this.ro_eje).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} %
          </v-progress-circular>
          
        </v-card-text>
        <v-chip class="ma-1" color="grey darken-3" label>
            <v-icon left>
              mdi-cash-multiple
            </v-icon>
            <span class="text-h7 font-weight-light">PIA: S/. {{ parseFloat(this.ejec[0][0]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>

        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">PIM: S/. {{ parseFloat(this.ejec[0][1]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Certificado: S/. {{ parseFloat(this.ejec[0][2]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Devengado: S/. {{ parseFloat(this.ejec[0][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">SALDO: S/. {{ parseFloat(this.ejec[0][1]-this.ejec[0][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>


        </v-card>
      </v-flex>

      <v-flex xs4 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto"
        color="blue darken-2"
        dark
        height="500"
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-chart-pie
          </v-icon>
          <span class="text-h6 font-weight-bold">% de Ejecución por fuente RDR</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Ejecución Recursos Directamente Recaudados
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-center">
          <v-progress-circular
            show-value
            :rotate="270"
            :size="290"
            :width="40"
            :thickness="0.4"
            :value="this.ejec[1][4]"
            color="cyan accent-1"
          >
            {{ parseFloat(this.ejec[1][4]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} %
          </v-progress-circular>
          
        </v-card-text>
        <v-chip class="ma-1" color="grey darken-3" label>
            <v-icon left>
              mdi-cash-multiple
            </v-icon>
            <span class="text-h7 font-weight-light">PIA: S/. {{ parseFloat(this.ejec[1][0]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>

        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">PIM: S/. {{ parseFloat(this.ejec[1][1]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Certificado: S/. {{ parseFloat(this.ejec[1][2]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Devengado: S/. {{ parseFloat(this.ejec[1][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">SALDO: S/. {{ parseFloat(this.ejec[1][1]-this.ejec[1][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        </v-card>
      </v-flex>
    </v-layout>


    <v-layout class="elevation-1 pa-2">
      <v-flex xs4 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto"
        color="blue darken-2"
        dark
        height="500"
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-chart-pie
          </v-icon>
          <span class="text-h6 font-weight-bold">% de Ejecución por fuente ROOC</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Recursos por Operaciones Oficiales de Credito
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-center">
          <v-progress-circular
            show-value
            :rotate="270"
            :size="290"
            :width="40"
            :thickness="0.4"
            :value="this.ejec[2][4]"
            color="cyan accent-1"
          >
            {{ parseFloat(this.ejec[2][4]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} %
          </v-progress-circular>
          
        </v-card-text>
        <v-chip class="ma-1" color="grey darken-3" label>
            <v-icon left>
              mdi-cash-multiple
            </v-icon>
            <span class="text-h7 font-weight-light">PIA: S/. {{ parseFloat(this.ejec[2][0]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>

        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">PIM: S/. {{ parseFloat(this.ejec[2][1]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Certificado: S/. {{ parseFloat(this.ejec[2][2]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Devengado: S/. {{ parseFloat(this.ejec[2][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">SALDO: S/. {{ parseFloat(this.ejec[2][1]-this.ejec[2][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>


        </v-card>
      </v-flex>


      <v-flex xs4 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto"
        color="blue darken-2"
        dark
        height="500"
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-chart-pie
          </v-icon>
          <span class="text-h6 font-weight-bold">% de Ejecución por fuente DT</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Ejecución Donaciones y Transferencias
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-center">
          <v-progress-circular
            show-value
            :rotate="270"
            :size="290"
            :width="40"
            :thickness="0.4"
            :value="this.ejec[3][4]"
            color="cyan accent-1"
          >
            {{ parseFloat(this.ejec[3][4]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} %
          </v-progress-circular>
          
        </v-card-text>
        <v-chip class="ma-1" color="grey darken-3" label>
            <v-icon left>
              mdi-cash-multiple
            </v-icon>
            <span class="text-h7 font-weight-light">PIA: S/. {{ parseFloat(this.ejec[3][0]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>

        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">PIM: S/. {{ parseFloat(this.ejec[3][1]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Certificado: S/. {{ parseFloat(this.ejec[3][2]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Devengado: S/. {{ parseFloat(this.ejec[3][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">SALDO: S/. {{ parseFloat(this.ejec[3][1]-this.ejec[3][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>


        </v-card>
      </v-flex>

      <v-flex xs4 class="mt-0 mr-2 elevation-10">
        <v-card
        class="mx-auto"
        color="blue darken-2"
        dark
        height="500"
        >
        <v-card-title>
          <v-icon
            large
            left
          >
          mdi-chart-pie
          </v-icon>
          <span class="text-h6 font-weight-bold">% de Ejecución por fuente RD</span>
        </v-card-title>
        <v-card-subtitle class="pb-0">
          Ejecución Recursos Determinados
        </v-card-subtitle>
        <v-card-text class="text-h4 font-weight-bold text-lg-center">
          <v-progress-circular
            show-value
            :rotate="270"
            :size="290"
            :width="40"
            :thickness="0.4"
            :value="this.ejec[4][4]"
            color="cyan accent-1"
          >
            {{ parseFloat(this.ejec[4][4]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} %
          </v-progress-circular>
          
        </v-card-text>
        <v-chip class="ma-1" color="grey darken-3" label>
            <v-icon left>
              mdi-cash-multiple
            </v-icon>
            <span class="text-h7 font-weight-light">PIA: S/. {{ parseFloat(this.ejec[4][0]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>

        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">PIM: S/. {{ parseFloat(this.ejec[4][1]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Certificado: S/. {{ parseFloat(this.ejec[4][2]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">Devengado: S/. {{ parseFloat(this.ejec[4][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        <v-chip class="ma-1" color="grey darken-3" label>
          <v-icon left>
            mdi-cash-multiple
          </v-icon>
          <span class="text-h7 font-weight-light">SALDO: S/. {{ parseFloat(this.ejec[4][1]-this.ejec[4][3]).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}</span>
        </v-chip>
        </v-card>
      </v-flex>
    </v-layout>


    </v-container>
  </template>
  
  <script>
    import axios from "axios";
    let url='http://localhost:8000/api/';

    export default {
      name: 'cmp_home',
      mounted(){
        this.get_totales();
        this.get_ejec_fuente();
      },
      
      data: () => ({
        ds_tot:[],
        ds_eje:[],
        ro_eje:'',
        ds_prog:[],
        ejec:[
        [0,0,0,0,0],
        [0,0,0,0,0],
        [0,0,0,0,0],
        [0,0,0,0,0],
        [0,0,0,0,0]
        ]

      }),

      methods:{
        limpiar: function(){
          for(var i=0;i<5;i++){
            for(var k=0;k<5;k++){
              this.ejec[i][k]=0;
            }
          }
        },
        async get_programas(){
            try {
                let datos=await axios.get(url+'programas')
                this.ds_prog= await datos.data;    
            } catch (error) {
                console.log(error);
            }
        },
        async get_totales(){
            try {
                let datos=await axios.get(url+'totales')
                this.ds_tot= await datos.data;
            } catch (error) {
                console.log(error);
            }
        },
        async get_ejec_fuente(){
            try {
                let datos=await axios.get(url+'ejec_fuente')
                this.ds_eje= await datos.data;
                this.limpiar();
                for(var i of this.ds_eje){
                  console.log(i.cod_fuente);
                  switch(i.cod_fuente){
                    case 1:
                          this.ro_eje=i.ejec;
                          this.ejec[0][0]=i.pia;
                          this.ejec[0][1]=i.pim;
                          this.ejec[0][2]=i.certif;
                          this.ejec[0][3]=i.deven;
                          this.ejec[0][4]=i.ejec;break;
                    
                    case 2:this.ejec[1][0]=i.pia;
                          this.ejec[1][1]=i.pim;
                          this.ejec[1][2]=i.certif;
                          this.ejec[1][3]=i.deven;
                          this.ejec[1][4]=i.ejec;break;

                    case 3:this.ejec[2][0]=i.pia;
                          this.ejec[2][1]=i.pim;
                          this.ejec[2][2]=i.certif;
                          this.ejec[2][3]=i.deven;
                          this.ejec[2][4]=i.ejec;break;
                          
                    case 4:this.ejec[3][0]=i.pia;
                          this.ejec[3][1]=i.pim;
                          this.ejec[3][2]=i.certif;
                          this.ejec[3][3]=i.deven;
                          this.ejec[3][4]=i.ejec;break;

                    case 5:this.ejec[4][0]=i.pia;
                          this.ejec[4][1]=i.pim;
                          this.ejec[4][2]=i.certif;
                          this.ejec[4][3]=i.deven;
                          this.ejec[4][4]=i.ejec;break;
                  }
                }
                console.log('ro:'+this.ejec[0][4]);
                console.log(this.ejec);
            } catch (error) {
                console.log(error);
            }
        },
      }
    }
  </script>
  
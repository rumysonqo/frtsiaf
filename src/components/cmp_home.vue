<template>
    <v-container fluid>
      <v-layout class="elevation-1 pa-2">
        <v-flex>
          <spam class="text-h5 font-weight-light">Montos Totales de Ejecución Presupuestal</spam>
        </v-flex>
      </v-layout>
      <v-layout class="elevation-9 pa-2">
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
        <v-card-text class="text-h5 font-weight-bold text-lg-right">
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
        <v-card-text class="text-h5 font-weight-bold text-lg-right">
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
        <v-card-text class="text-h5 font-weight-bold text-lg-right">
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
        <v-card-text class="text-h5 font-weight-bold text-lg-right">
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
        <v-card-text class="text-h5 font-weight-bold text-lg-right">
          S/. {{ parseFloat(this.ds_tot[0].saldo).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}
        </v-card-text>


        </v-card>
      </v-flex>
    </v-layout>

    <v-layout class="elevation-1 pa-2">
      <v-flex>
        <spam class="text-h5 font-weight-light">% de Ejecución Total y por Fuente de Financiamiento</spam>
      </v-flex>
    </v-layout>


    <v-layout class="elevation-9 pa-2">
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


    <v-layout class="elevation-9 pa-2">
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


    <v-layout class="elevation-1 pa-2">
      <v-flex>
        <spam class="text-h5 font-weight-light">% de Ejecución por Fuente y Generica de Gasto </spam>
      </v-flex>
    </v-layout>
    

    <v-layout class="elevation-5 pa-0">
      
      <v-tabs
      background-color="light-blue darken-4"
      center-active
      dark
      >

      <v-tabs-slider color="teal accent-2"></v-tabs-slider>
      

        <v-tab href="#fte1">
          <spam class="font-weight-bold">Recursos Ordinarios (RO)</spam>
          
        </v-tab>

        <v-tab-item value="fte1">
          <v-layout class="elevation-5 pa-5">
            <v-flex  xs12>
            
              <v-simple-table dense class="elevation-5">
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left teal darken-3 white--text text-center">
                      Generica
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIA
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIM
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Certificado
                    </th>
                    <th class=" text-left teal darken-3 white--text text-center">
                      Devengado
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por certificar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por devengar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      % Ejec.
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="item in ds_fte1"
                    :key="item.cod_fuente"
                  >
                    <td>{{ item.generica }}</td>
                    <td class="text-right">{{ parseFloat(item.pia).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.pim).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.certif).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.deven).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_cert).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_dev).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>

                    <td>
                        <div class="pa-2">
                        <v-progress-circular
                        show-value
                        :rotate="270"
                        :size="170"
                        :width="40"
                        :value="item.ejec"
                        color="teal darken-3"
                      >
                      <span class="text-h6 font-weight-bold">
                        {{ parseFloat(item.ejec).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}%
                      </span>
                      </v-progress-circular>
                    </div>
                    </td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
            
            </v-flex>
          </v-layout>
        </v-tab-item>

        <v-tab href="#fte2">
          <spam class="font-weight-bold">Recursos Directamente Recaudados (RDR)</spam>
        </v-tab>
        <v-tab-item value="fte2">
          <v-layout class="elevation-5 pa-5">
            <v-flex  xs12>
            
              <v-simple-table dense class="elevation-5">
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left teal darken-3 white--text text-center">
                      Generica
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIA
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIM
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Certificado
                    </th>
                    <th class=" text-left teal darken-3 white--text text-center">
                      Devengado
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por certificar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por devengar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      % Ejec.
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="item in ds_fte2"
                    :key="item.cod_fuente"
                  >
                    <td>{{ item.generica }}</td>
                    <td class="text-right">{{ parseFloat(item.pia).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.pim).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.certif).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.deven).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_cert).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_dev).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td>
                        <div class="pa-2">
                        <v-progress-circular
                        show-value
                        :rotate="270"
                        :size="170"
                        :width="40"
                        :value="item.ejec"
                        color="teal darken-3"
                      >
                      <span class="text-h6 font-weight-bold">
                        {{ parseFloat(item.ejec).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}%
                      </span>
                      </v-progress-circular>
                    </div>
                    </td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
            
            </v-flex>
          </v-layout>
        </v-tab-item>

        <v-tab href="#fte3">
          <spam class="font-weight-bold">Recursos por Operaciones Oficiales de Credito</spam>
        </v-tab>

        <v-tab-item value="fte3">
          <v-layout class="elevation-5 pa-5">
            <v-flex  xs12>
            
              <v-simple-table dense class="elevation-5">
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left teal darken-3 white--text text-center">
                      Generica
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIA
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIM
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Certificado
                    </th>
                    <th class=" text-left teal darken-3 white--text text-center">
                      Devengado
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por certificar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por devengar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      % Ejec.
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="item in ds_fte3"
                    :key="item.cod_fuente"
                  >
                    <td>{{ item.generica }}</td>
                    <td class="text-right">{{ parseFloat(item.pia).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.pim).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.certif).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.deven).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_cert).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_dev).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td>
                        <div class="pa-2">
                        <v-progress-circular
                        show-value
                        :rotate="270"
                        :size="170"
                        :width="40"
                        :value="item.ejec"
                        color="teal darken-3"
                      >
                      <span class="text-h6 font-weight-bold">
                        {{ parseFloat(item.ejec).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}%
                      </span>
                      </v-progress-circular>
                    </div>
                    </td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
            
            </v-flex>
          </v-layout>
        </v-tab-item>


        <v-tab href="#fte4">
          <spam class="font-weight-bold">Donaciones y Transferencias</spam>
        </v-tab>

        <v-tab-item value="fte4">
          <v-layout class="elevation-5 pa-5">
            <v-flex  xs12>
            
              <v-simple-table dense class="elevation-5">
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left teal darken-3 white--text text-center">
                      Generica
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIA
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIM
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Certificado
                    </th>
                    <th class=" text-left teal darken-3 white--text text-center">
                      Devengado
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por certificar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por devengar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      % Ejec.
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="item in ds_fte4"
                    :key="item.cod_fuente"
                  >
                    <td>{{ item.generica }}</td>
                    <td class="text-right">{{ parseFloat(item.pia).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.pim).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.certif).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.deven).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_cert).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_dev).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td>
                        <div class="pa-2">
                        <v-progress-circular
                        show-value
                        :rotate="270"
                        :size="170"
                        :width="40"
                        :value="item.ejec"
                        color="teal darken-3"
                      >
                      <span class="text-h6 font-weight-bold">
                        {{ parseFloat(item.ejec).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}%
                      </span>
                      </v-progress-circular>
                    </div>
                    </td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
            
            </v-flex>
          </v-layout>
        </v-tab-item>

        <v-tab href="#fte5">
          <spam class="font-weight-bold">Recursos Determinados</spam>
        </v-tab>

        <v-tab-item value="fte5">
          <v-layout class="elevation-5 pa-5">
            <v-flex  xs12>
            
              <v-simple-table dense class="elevation-5">
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left teal darken-3 white--text text-center">
                      Generica
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIA
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      PIM
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Certificado
                    </th>
                    <th class=" text-left teal darken-3 white--text text-center">
                      Devengado
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por certificar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      Saldo (por devengar)
                    </th>
                    <th class="text-left teal darken-3 white--text text-center">
                      % Ejec.
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="item in ds_fte5"
                    :key="item.cod_fuente"
                  >
                    <td>{{ item.generica }}</td>
                    <td class="text-right">{{ parseFloat(item.pia).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.pim).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.certif).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.deven).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_cert).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_dev).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td>
                        <div class="pa-2">
                        <v-progress-circular
                        show-value
                        :rotate="270"
                        :size="170"
                        :width="40"
                        :value="item.ejec"
                        color="teal darken-3"
                      >
                      <span class="text-h6 font-weight-bold">
                        {{ parseFloat(item.ejec).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}%
                      </span>
                      </v-progress-circular>
                    </div>
                    </td>
                  </tr>
                </tbody>
              </template>
            </v-simple-table>
            
            </v-flex>
          </v-layout>
        </v-tab-item>

      </v-tabs>


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
        this.get_ejec_generica();
        this.get_ejec_fte_gen(1);
        this.get_ejec_fte_gen(2);
        this.get_ejec_fte_gen(3);
        this.get_ejec_fte_gen(4);
        this.get_ejec_fte_gen(5);

      },
      
      data: () => ({
        ds_tot:[],
        ds_eje:[],
        ds_eje_gen:[],
        ro_eje:'',
        ds_fte1:[],
        ds_fte2:[],
        ds_fte3:[],
        ds_fte4:[],
        ds_fte5:[],
        ejec:[
        [0,0,0,0,0],
        [0,0,0,0,0],
        [0,0,0,0,0],
        [0,0,0,0,0],
        [0,0,0,0,0]
        ],
        eje_23:'',
        ds_siaf:[],
        ejec_gen:[
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
        limpiar_gen: function(){
          for(var i=0;i<5;i++){
            for(var k=0;k<5;k++){
              this.ejec_gen[i][k]=0;
            }
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

        async get_ejec_generica(){
            try {
                let datos=await axios.get(url+'ejec_generica')
                this.ds_eje_gen= await datos.data;
                this.limpiar_gen();
                for(var i of this.ds_eje_gen){
                  console.log(i.cod_generica);
                  switch(i.cod_generica){
                    case 1:
                          
                          this.ejec_gen[0][0]=i.pia;
                          this.ejec_gen[0][1]=i.pim;
                          this.ejec_gen[0][2]=i.certif;
                          this.ejec_gen[0][3]=i.deven;
                          this.ejec_gen[0][4]=i.ejec;break;
                    
                    case 2:this.ejec_gen[1][0]=i.pia;
                          this.ejec_gen[1][1]=i.pim;
                          this.ejec_gen[1][2]=i.certif;
                          this.ejec_gen[1][3]=i.deven;
                          this.ejec_gen[1][4]=i.ejec;break;

                    case 3:this.eje_23=i.ejec;
                          this.ejec_gen[2][0]=i.pia;
                          this.ejec_gen[2][1]=i.pim;
                          this.ejec_gen[2][2]=i.certif;
                          this.ejec_gen[2][3]=i.deven;
                          this.ejec_gen[2][4]=i.ejec;break;
                          
                    case 5:this.ejec_gen[3][0]=i.pia;
                          this.ejec_gen[3][1]=i.pim;
                          this.ejec_gen[3][2]=i.certif;
                          this.ejec_gen[3][3]=i.deven;
                          this.ejec_gen[3][4]=i.ejec;break;

                    case 6:this.ejec_gen[4][0]=i.pia;
                          this.ejec_gen[4][1]=i.pim;
                          this.ejec_gen[4][2]=i.certif;
                          this.ejec_gen[4][3]=i.deven;
                          this.ejec_gen[4][4]=i.ejec;break;
                  }
                }
                console.log('ro:'+this.ejec[0][4]);
                console.log(this.ejec);
            } catch (error) {
                console.log(error);
            }
        },

        async get_ejec_fte_gen($fte){
            try {
                let datos=await axios.get(url+'ejec_fte_gen/'+$fte)
                switch($fte){
                  case 1:this.ds_fte1=await datos.data;break;
                  case 2:this.ds_fte2=await datos.data;break;
                  case 3:this.ds_fte3=await datos.data;break;
                  case 4:this.ds_fte4=await datos.data;break;
                  case 5:this.ds_fte5=await datos.data;break;
                }
                //this.ds_siaf= await datos.data;
                //console.log('ds_siaf');
                //console.log(this.ds_siaf);
            } catch (error) {
                console.log(error);
            }
        }

      }
    }
  </script>
  
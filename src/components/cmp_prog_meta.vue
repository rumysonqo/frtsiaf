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
                    dense
                    @change="get_programa_meta()"
                  >
                  </v-select>
            
                </v-flex>
        
        </v-layout>
    
        <v-layout class="elevation-1 pa-2">
          <v-flex>
            <spam class="text-h5 font-weight-light">% de Ejecución por Meta</spam>
          </v-flex>
        </v-layout>



        <v-layout>
            <v-flex  xs12>
            
              <v-simple-table dense class="elevation-5">
              <template v-slot:default>
                <thead>
                  <tr>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      Meta
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      PIA
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      PIM
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      Certificado
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      Saldo (por certificar)
                    </th>
                    <th class=" text-left blue darken-3 accent-4 white--text text-center">
                      Devengado
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      Saldo (por devengar)
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      % Ejec.
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      Meta Fisica
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      Avance
                    </th>
                    <th class="text-left blue darken-3 accent-4 white--text text-center">
                      % Avance (junio)
                    </th>

                  </tr>
                </thead>
                <tbody>
                  <tr
                    v-for="item in ds_siaf"
                    :key="item.cod_meta"
                  >
                    <td>{{ item.meta }}</td>
                    <td class="text-right">{{ parseFloat(item.pia).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.pim).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.certif).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_cer).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right">{{ parseFloat(item.deven).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td class="text-right font-weight-bold">{{ parseFloat(item.sal_dev).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} </td>
                    <td>
                        <div class="pa-2">
                        <v-progress-circular
                        show-value
                        :rotate="270"
                        :size="100"
                        :width="20"
                        :value="item.ejec"
                        color="deep-purple darken-4"
                      >
                        {{ parseFloat(item.ejec).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}}%
                      </v-progress-circular>
                    </div>
                      
                    </td>
                    <td class="text-right">{{ parseFloat(item.meta_fisica).toLocaleString('en-us', { minimumFractionDigits: 0, maximumFractionDigits: 0 })}}</td>
                    <td class="text-right">{{ parseFloat(item.avance).toLocaleString('en-us', { minimumFractionDigits: 0, maximumFractionDigits: 0 }) }}</td>
                    <td>
                      <div>
                      <v-progress-circular
                      show-value
                      :rotate="270"
                      :size="100"
                      :width="20"
                      :thickness="0.4"
                      :value="item.porc_avance"
                      color="teal darken-2"
                      >
                      {{ parseFloat(item.porc_avance).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 })}} %
                      </v-progress-circular>  
                    </div>
                    </td>

                  </tr>
                </tbody>
              </template>
            </v-simple-table>
            
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
            this.get_programas();
            this.get_programa_meta();
    
          },
          
          data: () => ({
            ds_tot:[0,0,0,0,0,0],
            ds_eje:[],
            ds_eje_gen:[],
            ro_eje:'',
            cod_prg:1,
            ds_prog:[],
            ds_siaf:[],
            headers:[{
            text:'META',
            align:'start',
            value:'meta',
            class:'blue darken-3 white--text',
            },

            { align: 'right', text: 'PIM', value: 'pim',format:val=>parseFloat(val).toLocaleString('en-us', { minimumFractionDigits: 2, maximumFractionDigits: 2 }),headerStyle: {fontSize: '1.2em'},style: {fontSize: '1em'} },
            
            {
            text:'DEVENGADO',
            align:'center',
            filterable: false,
            value:'deven',
            class:'blue darken-3 white--text',
            },
            { align: 'right', text: '%EJEC', value: 'ejec'},
            
            {
            text:'META FISICA',
            align:'center',
            filterable: false,
            value:'meta_fisica',
            class:'blue darken-3 white--text'
            },
            {
            text:'AVANCE',
            align:'start',
            filterable: false,
            value:'avance',
            class:'blue darken-3 white--text'
            },
            {
            text:'% AVANCE',
            align:'start',
            filterable: false,
            value:'porc_avance',
            class:'blue darken-3 white--text'
            }]
    
          }),
    
          methods:{
            formato(value) {
                let val = (value/1).toFixed(2).replace('.', ',')
                return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".")
            },
            async get_programas(){
                try {
                    let datos=await axios.get(url+'programas')
                    this.ds_prog= await datos.data;    
                } catch (error) {
                    console.log(error);
                }
            },
    
            async get_programa_meta(){
                try {
                    let datos=await axios.get(url+'ejec_meta/'+this.cod_prg)
                    this.ds_siaf= await datos.data;
                } catch (error) {
                    console.log(error);
                }
            }
    
          }
        }
      </script>
      

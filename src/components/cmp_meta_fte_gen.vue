<template>
    <v-container fluid>
        <v-layout>
            <v-flex xs4 class="pr-2">
                <v-select
                    v-model="cod_prg"
                    :items=ds_prog
                    item-text="programa"
                    item-value="cod_programa"
                    label="Seleccione un programa"
                    outlined
                    dense
                    @change="get_ejec_meta_gen_fte()"
                  >
                  </v-select>
            
                </v-flex>
                <v-flex xs4 class="pr-2">
                    <v-select
                        v-model="cod_gen"
                        :items=ds_gen
                        item-text="generica"
                        item-value="cod_generica"
                        label="Seleccione una generica de gasto"
                        outlined
                        dense
                        @change="get_ejec_meta_gen_fte()"
                      >
                      </v-select>
                
                    </v-flex>
                    <v-flex xs4>
                        <v-select
                            v-model="cod_fte"
                            :items=ds_fte
                            item-text="fuente"
                            item-value="cod_fuente"
                            label="Seleccione una fuente de financiamiento"
                            outlined
                            dense
                            @change="get_ejec_meta_gen_fte()"
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
                    <th class="text-left blue darken-3 accent-4 white--text text-center" style="width:500px;">
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
                    <th class="text-left blue darken-3 accent-4 white--text text-center" style="width:300px;">
                      % Ejec.
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
                    <td class="text-center">
                        <div class="pa-2">
                        <v-progress-circular
                        show-value
                        :rotate="270"
                        :size="120"
                        :width="20"
                        :value="item.ejec"
                        color="teal darken-1"
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
    
        </v-container>
    
    
    
    
    
      </template>
      
      <script>
        import axios from "axios";
        let url='http://localhost:8000/api/';
    
        export default {
          name: 'cmp_home',
          mounted(){
            this.get_programas();
            this.get_genericas();
            this.get_fuentes();
            this.get_programa_meta();
            this.get_ejec_meta_gen_fte();
    
          },
          
          data: () => ({
            ds_tot:[0,0,0,0,0,0],
            ds_eje:[],
            ds_eje_gen:[],
            ro_eje:'',
            cod_prg:1,
            cod_gen:3,
            cod_fte:1,
            ds_prog:[],
            ds_gen:[],
            ds_fte:[],
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
            async get_genericas(){
                try {
                    let datos=await axios.get(url+'genericas')
                    this.ds_gen= await datos.data;    
                } catch (error) {
                    console.log(error);
                }
            },
            async get_fuentes(){
                try {
                    let datos=await axios.get(url+'fuentes')
                    this.ds_fte= await datos.data;    
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
            },

            async get_ejec_meta_gen_fte(){
                try {
                    this.ds_siaf=[];
                    let datos=await axios.get(url+'ejec_meta_gen_fte/'+this.cod_prg+"/"+this.cod_gen+"/"+this.cod_fte)
                    this.ds_siaf= await datos.data;
                } catch (error) {
                    console.log(error);
                }
            }
    
          }
        }
      </script>
      

<template>
    
    <md-table v-model="items" md-card md-fixed-header>
        <md-table-toolbar>
            <div class="md-toolbar-section-start md-layout-item">
                <div class="md-headline">Últimas avaliações</div>
            </div>
            <div class="md-layout-item md-size-10">
                <md-field>
                    <md-select v-model="date" name="font" id="font" md-dense>
                        <md-option value="hoje">Hoje</md-option>
                        <md-option value="ontem">Ontem</md-option>
                        <md-option value="ultimas semanas">Ultimas semanas</md-option>
                    </md-select>
                </md-field>
            </div>
        </md-table-toolbar>

        <md-table-row>
            <md-table-head class="table-title">Dados do veículo</md-table-head>
            <md-table-head class="table-title">Valor</md-table-head>
            <md-table-head class="table-title">Status</md-table-head>
        </md-table-row>

        <md-table-row v-for="(item, i) in items" :key="i">
            <md-table-cell style="padding-left: 20px;">
                <div class="md-layout" style="padding-right: 0">
                    <figure class="md-layout-item table-figure">
                        <img :src="item.image" alt="" width="100%">
                    </figure>
                    <div class="md-layout-item infos">
                        <strong>{{ item.name }}</strong>
                        <p>{{ item.version_name }}</p>
                        <p>{{ item.model_year }} - {{ item.fuel_type }}</p>
                        <p class="">{{ item.transmission_type}} - {{ item.mileage }}</p>
                    </div>
                </div>
            </md-table-cell>
            <md-table-cell>
                <p>ANÚNCIO</p>
                <input type="hidden" v-model.lazy="item.ad_selling_price" v-money="money" />
                <p><strong>{{ item.ad_selling_price }}</strong></p>
                <!-- Não encontrei as informações abaixo -->
                <p>MÍNIMO ACEITO</p>
                <p>R$ 115.560</p>
            </md-table-cell>
            <md-table-cell>
                <p class="center-align"><span class="chip">Aguardando precificação</span></p>
                <p class="center-align">2020 às 14:35</p>
            </md-table-cell>
        </md-table-row>
       <md-table-row>
            <md-table-cell colspan="4" style="padding: 0">
                <p class="right-align"><a href="javascript:void(0);">Ver tudo <i class="material-icons">arrow_right</i></a></p>
            </md-table-cell>
        </md-table-row>
    </md-table>
    
</template>
<script>
import axios from 'axios';
import {VMoney} from 'v-money'

export default {
    data() {
        return {
            items: [],
            date: 'hoje',
            money: {
                decimal: ',',
                thousands: '.',
                prefix: 'R$ ',
                suffix: '',
                precision: 2
            }
        }
    },
    
    directives: { money: VMoney },

    mounted() {
        axios.get('http://www.mocky.io/v2/5eb553df31000060006994a8')
        .then((resp) => {
            this.items = resp.data;
        })
    }
}
</script>
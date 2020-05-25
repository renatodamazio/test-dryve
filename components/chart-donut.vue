<template>
    <md-card>
        <md-subheader class="md-subheader-black">Preços - Dryve x KBB</md-subheader>
        <md-card-content>
            <vc-donut
                background="white" foreground="grey"
                :size="140" unit="px" :thickness="30"
                has-legend legend-placement="right"
                :sections="sections" :total="100"
                :start-angle="0" :auto-adjust-text-size="true"
                @section-click="handleSectionClick">
            </vc-donut>
        </md-card-content>
    </md-card>
</template>
<style lang="scss">
    .md-subheader-black {
        color: rgba(0, 0, 0, 0.87) !important;
        font-weight: 500;
    }

    .cdc-container {
        flex-direction: row !important;
    }

    .cdc-overlay {
        width: 115px !important;
        height: 115px !important;
        top: 50% !important;
        left: 50% !important;
        transform: translate(-50%, -50%);
    }

    .cdc-legend {
        justify-content: flex-start;
        span {
            font-size: 14px;
            font-weight: 500;
            font-stretch: normal;
            font-style: normal;
            line-height: normal;
            letter-spacing: 0.1px;
            color: rgba(0, 0, 0, 0.87);
            justify-content: flex-start !important;
        }
    }

    .cdc-legend-item-color {
        border-radius: 100%;
        width: 8px;
        height: 8px;
    }
</style>
<script>
    import Vue from 'vue';
    import Donut from 'vue-css-donut-chart';
    import 'vue-css-donut-chart/dist/vcdonut.css';
    Vue.use(Donut);

    export default {
         data() {
        return {
            sections: [
                { label: 'Na média', value: 60, color: '#1070ca' },
                { label: 'Acima da média', value: 25, color: '#ec4c47' },
                { label: 'Abaixo da média', value: 15, color: '#f7d154' }
            ]
        };
        },
        methods: {
        handleSectionClick(section, event) {
            console.log(`${section.label} clicked.`);
        }
        }
    }
</script>
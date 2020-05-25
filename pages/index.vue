<template>
  <div>
    <div class="main-header md-layout md-gutter">
      <div v-for="(card, i) in cards" :key="i" class="md-layout-item">
        <CardQuickInfo 
          prefecth
          :title="card.title"
          :value="card.value"
          :icon="card.icon"
          :footer_icon="card.footer_icon"
          :footer_text="card.footer_text"
          :footer_estimative="card.footer_estimative"
          :footer_status="card.footer_status"
        />
      </div>
    </div>
    
    <div class="md-layout md-gutter">
      <div class="md-layout-item md-size-66">
        <Evaluations />
      </div>
      <div class="md-layout-item md-size-44">
        <div class="mb-30">
          <CardInfo />
        </div>
        <ChartDonut />
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        cards: [{
          title: 'AVALIAÇÕES HOJE',
          value: '90',
          icon: 'drive_eta',
          footer_icon: 'arrow_drop_up',
          footer_text: 'Hoje',
          footer_estimative: '40',
          footer_status: 'regular'
        },{
          title: 'CARROS PUBLICADOS',
          value: '397',
          icon: 'important_devices',
          footer_icon: 'arrow_drop_up',
          footer_text: 'este mês',
          footer_estimative: '4',
          footer_status: 'regular'
        },{
          title: 'TICKET MÉDIO DO ESTOQUE',
          value: 'R$ 42.567',
          icon: 'attach_money',
          footer_icon: 'arrow_drop_up',
          footer_text: 'Hoje',
          footer_estimative: '40',
          footer_status: 'regular'
        }]
      }
    },
    components: {
      CardQuickInfo: () => import('../components/card-quick-info.vue'),
      Evaluations: () => import('../components/Evaluations.vue'),
      CardInfo: () => import('../components/card-info.vue'),
      ChartDonut: () => import('../components/chart-donut.vue')
    }
  }
</script>

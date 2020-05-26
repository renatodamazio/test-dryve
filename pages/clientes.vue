<template>
    <div>
        <div class="main-header">
            <div class="md-layout gutter" style="width: 100%">
                <div class="md-layout-item md-size-10">
                    <md-menu md-direction="bottom-start" class="bt-regular">
                        <md-button md-menu-trigger>
                        <md-icon>filter_list</md-icon> FILTRAR
                        </md-button>

                        <md-menu-content>
                            <md-menu-item @click="data = 'click 1'">My Item 1</md-menu-item>
                            <md-menu-item @click="data = 'click 1'">My Item 2</md-menu-item>
                            <md-menu-item @click="data = 'click 1'">My Item 3</md-menu-item>
                        </md-menu-content>
                    </md-menu>
                </div>
                <div class="md-layout-item md-size-30 pl-10">
                    <md-field class="regular-field">
                        <md-input></md-input>
                        <md-icon>search</md-icon>
                    </md-field>
                </div>
                <div class="md-layout-item">
                    <md-button class="md-raised md-purple m-0 right-align" style="float: right">
                        <md-icon>add</md-icon>Adicionar
                    </md-button>
                </div>
            </div>
        </div>
        <md-table v-model="people" md-card @md-selected="onSelect">
            <md-table-row slot="md-table-row" slot-scope="{ item }" :md-disabled="item.name.includes('Stave')" md-selectable="multiple" md-auto-select>
                <md-table-cell md-label="Nome" md-sort-by="name">{{ item.name }}</md-table-cell>
                <md-table-cell md-label="Status" md-sort-by="status">
                    <div v-if="item.status == 'Cliente'" class="table-badge primary">{{ item.status }}</div>
                    <div v-if="item.status == 'Lead'" class="table-badge">{{ item.status }}</div>
                </md-table-cell>
                <md-table-cell md-label="Telefone" md-sort-by="phone">{{ item.phone }}</md-table-cell>
                <md-table-cell md-label="E-mail" md-sort-by="email">{{ item.email }}</md-table-cell>
            </md-table-row>
        </md-table>
        <md-table class="table-footer">
            <md-table-row>
                <md-table-cell>
                    <div class="md-layout px-4 md-alignment-start-center pl-20" style="align-items: center;">
                        <span>Itens por página:</span>
                        <div class="">
                            <md-field style="max-width: 60px; margin-left: 10px">
                                <md-select v-model="filter">
                                    <md-option v-for="i in 100" :key="i" :value="i"> {{ i }} </md-option>
                                </md-select>
                            </md-field>
                        </div>
                        <span>
                            1-10 de 3.456
                        </span>
                    </div>
                </md-table-cell>
                <md-table-cell class="right-align">
                    <md-button class="button-small">
                        <md-icon><i class="material-icons">keyboard_arrow_left</i></md-icon>
                    </md-button>
                    <md-button class="button-small">
                        <md-icon><i class="material-icons">keyboard_arrow_right</i></md-icon>
                    </md-button>
                </md-table-cell>
        </md-table-row>
        </md-table>
    </div>
</template>
<style lang="scss" scoped>
    .table-badge {
        font-size: 12px;
        position: relative;
        max-width: 80px;
        height: 26px;
        text-align: center;
        line-height: 26px;
        border-radius: 13px;
        background-color: #f6f6f6;
        color: #666666;
        &.primary {
            color: #0065ff;
            background-color: #f3f7ff;
        }
    }
    .md-table {
        width: 100%;
        color: rgba(0, 0, 0, 0.87);
    }
    .md-table-head-label {
        padding-left: 0 !important;
    }
    .md-table-cell-container {
        font-size: 14px;
        font-size: 14px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: 1.71;
        letter-spacing: 0.1px;
        color: rgba(0, 0, 0, 0.87);
    }

    .md-field {
        padding: 0;
        margin: 0;
        height: 24px;
    }

    .button-small {
        width: 30px;
        height: 30px;
        min-width: auto;
    }

    .table-footer {
        border: solid 1px rgba(0, 0, 0, 0.12);
        border-top: 0;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        .md-table-cell {
            padding: 0;
        }
    }
</style>
<script>
    export default {
       data: () => ({
        selected: [],
        filter: 10,
        people: [
            {
                name: 'Paulo Henrique Matos',
                status: 'Cliente',
                phone: '(16) 99653-8899',
                email: 'ph.mattos@gmail.com'
            },
            {
                name: 'Juliana Martins Silva',
                status: 'Lead',
                phone: '(16) 99664-0187',
                email: 'a.vieira@uol.com.br'
            }
      ]
    }),
    methods: {
      onSelect (items) {
        this.selected = items
      },
      getAlternateLabel (count) {
        let plural = ''

        if (count > 1) {
          plural = 's'
        }

        return `${count} user${plural} selected`
      }
    }
  }
</script>
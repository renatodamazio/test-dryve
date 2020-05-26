<template>
    <header>
        <div class="md-layout">
            <div class="area-search" :class="showSearch ? 'is-visible' : ''">
                <md-button id="cancel-search" @click="showSearch = false"> 
                    <md-icon>cancel</md-icon>
                    <md-tooltip :md-active.sync="tooltipActive">Fechar a busca</md-tooltip>    
                </md-button>
                <md-autocomplete
                    v-model="search"
                    :md-options="suggestions"
                    md-layout="box"
                    md-dense>
                    <label>Pesquisar por...</label>
                </md-autocomplete>
            </div>
            <div class="md-layout-item">
                <div class="area-logo">
                    <img src="~/assets/images/logo.png" alt="" width="101" height="34">
                    <label for="">Backoffice</label>
                </div>
            </div>
            <div class="md-layout-item">
                <div class="area-buttons right-align">
                    <md-button class="round-button is-small" @click="showSearch = true"><md-icon>search</md-icon></md-button>
                    <md-button class="round-button is-small"><md-icon>notifications</md-icon></md-button>
                </div>
            </div>
        </div>
    </header>
</template>
<style lang="scss" scoped>
    header {
        background: #fff;
        z-index: 9999;
        box-shadow: 0 1px 0 0 #e0e0e0;
        padding: 20px 30px;
        position: relative;

        #cancel-search {
            max-width: 30px;
            min-width: auto;
            position: absolute;
            left: 16px;
            top: 16px;
            font-size: 30px
        }
    }

    .area-search {
        position: absolute;
        width: 100%;
        left: 0;
        top: 0;
        z-index: 999;
        height: 100%;
        opacity: 0;
        visibility: hidden;
        transition: .800s cubic-bezier(0.075, 0.82, 0.165, 1);

        &.is-visible {
            opacity: 1;
            visibility: visible;
        }
            .md-field {
                height: 65px;
                input {
                    padding-left: 66px;
                }
            }
            label {
                padding-left: 66px;
            }
    }

    .area-logo {
        label {
            font-size: 10px;
            font-weight: 500;
            font-stretch: normal;
            font-style: normal;
            line-height: 1;
            letter-spacing: normal;
            color: #a5abb7;
        }
    }

    .area-buttons {
        .round-button {
            border-radius: 100%;
            max-width: 20px;
            margin: 0;
            min-width: 36px;
            font-size: 14px;
            text-align: right;
        }

        .is-small {
            i {
                font-size: 18px !important;
                color: #a5abb7;
            }
        }
    }
</style>
<script>
export default {
    data() {
        return {
            showSearch: false,
            suggestions: [
                'Cadastrar clientes',
                'Novo veículo',
                'intenção de compra',
                'Dados do veículo'
            ]
        }
    }
}
</script>
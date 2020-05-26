<template>
    <nav>
        <ul>    
            <li>    
                <headerInfo></headerInfo>
            </li>
            <li class="navgation-area">
                <n-link to="/">
                    <i class="material-icons">home</i>
                    <span>Início</span>
                </n-link>
                <n-link to="/clientes">
                    <i class="material-icons">person</i>
                    <span>Clientes</span>
                </n-link>
                <n-link to="/">
                    <i class="material-icons">drive_eta</i>
                    <span>Veículos</span>
                </n-link>
                <n-link to="/">
                    <i class="material-icons">device_hub</i>
                    <span>Triangulação</span>
                </n-link>
                <n-link to="/">
                    <i class="material-icons">account_balance_wallet</i>
                    <span>Financeiro</span>
                </n-link>
            </li>
        </ul>
    </nav>
</template>
<style scoped lang="scss">
    .md-theme-default {
        nav {
            width: 80px;
            box-shadow: 1px 0 0 0 #e0e0e0;
            position: relative;
            z-index: 99999;
            &:hover {
            ul {
                width: 240px;
                a {
                    span {
                        opacity: 1;
                    }
                }
            }
            }

            ul {
                background: #fff;
                overflow: hidden;
                width: 100%;
                top: 0;
                left: 0;
                z-index: 9999;
                position: absolute;
                height: 100%;
                padding: 15px;
                box-shadow: 1px 0 0 0 #e0e0e0;
                transition: .300s ease-in-out;
            }

            a {
                padding: 10px 12px;
                white-space: nowrap;
                width: 100%;
                float: left;
                font-size: 14px;
                border-radius: 4px;
                line-height: 24px;
                align-content: center;
                font-weight: bold;
                display: flex;
                color: rgba(0, 0, 0, 0.87);

                &:hover {
                    background: #f3f7ff;
                    i {
                        opacity: 1;
                    }
                }

                i {
                    display: inline-block;
                    opacity: 0.5;
                }

                span {
                    padding-left: 20px;
                    opacity: 0;
                }
            }
        }
    }
</style>
<script>
export default {
    components: {
        headerInfo: () =>  import('./header-info.vue')
    }
}
</script>
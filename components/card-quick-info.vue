<template>
    <div class="card-expansion">
        <md-card>
            <md-card-header class="card-header">
                {{ title }}
            </md-card-header>
            <md-card-content>
                <div class="card-aside--data">
                    <h1>{{ value }}</h1>
                </div>

                <div class="card-aside--icon">
                    <i class="material-icons">{{ icon }}</i>
                </div>
            </md-card-content>

            <md-card-actions md-alignment="left" :class="footer_status != 'regular' ? 'down' : ''">
                <i class="material-icons">{{ footer_icon }}</i>
                <span>{{ footer_estimative }}%</span>
                <label>{{ footer_text }}</label>
            </md-card-actions>
        </md-card>
    </div>
</template>
<style scoped lang="scss">
      .md-card-header {
            font-size: 10px;
            color: rgba(0, 0, 0, 0.87);
            opacity: 0.5;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            font-weight: 500;
            width: 100%;
            padding: 9px 20px;
        }

        .md-card-content {
            padding-bottom: 0;
            display: flex;
            align-items: center;
            height: 32px;
            
            .card-aside {
                &--data {
                    flex-grow: 9;
                    h1 {
                        font-size: 34px;
                        font-weight: normal;
                        color: rgba(0, 0, 0, 0.87);
                    }
                }
                &--icon {
                    flex-grow: 1;
                    text-align: right;

                    i {
                        width: 64px;
                        height: 64px;
                        font-size: 34px;
                        color: #0065ff;
                        display: inline-block;
                        border-radius: 100%;
                        background-color: #f3f7ff;
                        line-height: 64px;
                        text-align: center;
                    }
                }
            }
        }

        .md-card-actions {
            font-weight: normal;
            font-stretch: normal;
            font-style: normal;
            line-height: 1.45;
            display: flex;
            align-items: center;
            letter-spacing: normal;

            i {
                color: #0065ff;
                width: 18px;
            }
            
            span {
                padding: 0 5px;
                font-size: 12px;
                color: #6200ee;
            }

            label {
                color: rgba(0, 0, 0, 0.87);
                opacity: 0.5;
                font-size: 11px;
            }

            &.down {
                i, span {
                    color: #fc4a40;
                }
            }
        }
</style>
<script>
export default {
    name: 'card-quick-vue',
    props: {
        title: {
            type: String,
            required: true
        },
        value: {
            type: String,
            required: true
        },
        icon: {
            type: String,
            required: true
        },
        
        footer_icon: {
            type: String,
            required: true
        },
        footer_text: {
            type: String,
            required: true
        },
        footer_estimative: {
            type: String,
            required: true
        },
        footer_status: {
            default: 'regular', //Low, high
            type: String
        }
    }
}
</script>
<template>
    <div>
        <div class="card">
            <span class="card-header">{{ title }}</span>
            <div class="card-body">
                <div class="card-aside--data">
                    <h1>{{ value }}</h1>
                </div>
                <div class="card-aside--icon">
                    <i class="material-icons">{{ icon }}</i>
                </div>
            </div>
            <div class="card-footer">
                <i class="material-icons">{{ footer_icon }}</i>
                <span>{{ footer_estimative }}%</span>
                <label>{{ footer_text }}</label>
            </div>
        </div>
    </div>
</template>
<style scoped lang="scss">
    .card {
        border-radius: 4px;
        background: #fff;
        display: flex;
        flex-direction: column;
        padding: 13px 22px;
        border: 1px solid rgba(0, 0, 0, 0.12);
        flex: 1;
        
        .card-header {
            font-size: 10px;
            color: rgba(0, 0, 0, 0.87);
            opacity: 0.5;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            font-weight: 500;
            width: 100%;
            float: left;
        }

        .card-body {
            display: flex;
            align-items: center;

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

        .card-footer {
            font-weight: normal;
            font-stretch: normal;
            font-style: normal;
            line-height: 1.45;
            display: flex;
            align-items: center;
            letter-spacing: normal;

            i {
                margin-left: -6px;
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
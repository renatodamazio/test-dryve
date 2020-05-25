<template>
    <div class="user-header">
        <figure><img :src="user.download_url" alt=""></figure>
        <div class="user-info">
            <strong>{{ user.author }}</strong>
            <n-link to="/" class="exit"><i class="material-icons">power_settings_new</i>  Sair  </n-link>
        </div>
    </div>
</template>
<style lang="scss" scoped>
    .user-header {
        white-space: nowrap;
        width: 300px;
        display: flex;
        padding-top: 31px;
        padding-bottom: 27px;
        align-items: center;

        figure {
            width: 50px;
            height: 50px;
            border-radius: 100%;
            display: inline-block;
            border: 2px solid #fff;
            box-shadow: 0px 0px 1px 2px #0065ff;
            background: #eee;
            overflow: hidden;

            img {
                object-fit: cover;
                width: 50px;
                height: 50px;
            }
        }

        strong {
            font-size: 14px;
            font-weight: 500;
            font-stretch: normal;
            font-style: normal;
            line-height: 1.14;
            letter-spacing: 0.1px;
            width: 100%;
            clear: both;
            float: left;
            color: rgba(0, 0, 0, 0.87);
        }

        .exit {
            font-size: 10px;
            font-weight: 500;
            font-stretch: normal;
            font-style: normal;
            line-height: 1;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            float: left;
            color: rgba(0, 0, 0, 0.87);
            margin-top: 5px;
            opacity: 0.5;

            i {
                font-size: 12px;
            }

        }

        .user-info {
            padding-left: 18px;
        }
    }
</style>
<script>
    import axios from 'axios';
    export default {
        data() {
            return {
                user: []
            }
        },

        mounted() {
            this.getProfile();
        },

        methods: {
            getProfile() {
                axios.get('https://picsum.photos/id/0/info')
                .then((resp) => {
                    this.user = resp.data
                })
            }
        }
    }
</script>
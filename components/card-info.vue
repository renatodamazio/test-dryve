<template>
    <md-list mx-size-100>
        <md-subheader>Top intenções de compra</md-subheader>

        <md-list-item v-for="i in 4" :key="i">
            <md-avatar>
                <img src="~/assets/images/rectangle@3x.png" width="100%">
            </md-avatar>

            <div class="md-list-item-text">HB20</div>

            <div>197</div>
      </md-list-item>

    </md-list>
</template>

<style lang="scss" scoped>
    .md-list-item {
        border-bottom: solid 1px rgba(0, 0, 0, 0.12);
        font-size: 14px;
        font-weight: 500;
        font-stretch: normal;
        font-style: normal;
        line-height: 1.71;
        letter-spacing: 0.1px;
        color: rgba(0, 0, 0, 0.87);
    }

    .md-avatar {
        width: 36px;
        height: 36px;
        border-radius: 4px;
        img {
            object-fit: contain;
        }
    }
</style>

<script>

export default {  
}
</script>
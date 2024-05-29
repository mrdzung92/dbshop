<template>
    <div class="trade-page">
        <div class="head">
            <div class="left"><img src="@/assets/images/btc.png" alt="btc">
                <p class="text">Btc<span class="curency">usdt</span></p>
            </div>
            <div class="right">
                <p class="text">USDT: <span class="coin">189373</span></p>
                <font-awesome-icon class="icon" :icon="['fas', 'rotate']" />
            </div>
        </div>
        <chart />
    </div>
</template>

<script>
import chart from './chart.vue';

export default {
    components: {
        chart
    }
}
</script>

<style lang="scss" scoped></style>
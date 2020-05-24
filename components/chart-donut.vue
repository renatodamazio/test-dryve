<template>
    <div>
        <canvas id="cart" width="130" height="130"></canvas>
    </div>
</template>
<style lang="scss" scoped>
    
</style>
<script>
    import Chart from 'chart.js';
    export default {
        data() {
            return {
               
            }
        },

        mounted() {
            this.init();
        },

        methods: {
            init() {
                var ctx = document.getElementById('cart');
                var myChart = new Chart(ctx, {
                    type: 'doughnut',
                    data: {
                            labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
                            datasets: [{
                                data: [12, 19, 3, 5, 2, 3],
                                backgroundColor: [
                                    'rgba(255, 99, 132, 1)',
                                    'rgba(54, 162, 235, 1)',
                                    'rgba(255, 206, 86, 1)',
                                    'rgba(75, 192, 192, 1)',
                                    'rgba(153, 102, 255, 1)',
                                    'rgba(255, 159, 64, 1)'
                                ],
                                borderColor: [
                                    'rgba(255, 99, 132, 1)',
                                    'rgba(54, 162, 235, 1)',
                                    'rgba(255, 206, 86, 1)',
                                    'rgba(75, 192, 192, 1)',
                                    'rgba(153, 102, 255, 1)',
                                    'rgba(255, 159, 64, 1)'
                                ],
                                borderWidth: 1
                            }]
                    },
                    options: {
                        legend: {
                            position: "top",
                            align: "end",
                            lineWidth: 1000
                        }
                    }
                })
            }
        }
    }
</script>
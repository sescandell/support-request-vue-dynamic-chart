<script>
    import { Bar, mixins } from 'vue-chartjs'
    const { reactiveData } = mixins;

    export default {
        extends: Bar,
        mixins: [reactiveData],
        props: {
            data: {
                type: Array,
                required: true
            }
        },
        data() {
            return {
                chartData: {
                    labels: (new Array(this.data.length)).fill(''),
                    datasets: [{
                        label: 'My dataset',
                        backgroundColor: 'rgba(250,0,0)',
                        data: this.data
                    }]
                }
            };
        },
        mounted() {
            this.renderChart(this.chartData, {
                maintainAspectRatio: false,
                legend: {
                    display: false
                },
                scales: {
                    xAxes: [{
                        display: false,
                        categoryPercentage: 1,
                        barPercentage: 0.5
                    }],
                    yAxes: [{
                        display: false
                    }]
                }
            })
        }
    }
</script>
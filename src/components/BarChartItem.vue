<script>
    import { Bar } from 'vue-chartjs'

    export default {
        extends: Bar,
        props: {
            data: {
                type: Array,
                required: true
            }
        },
        mounted() {
            this.renderChart({
                labels: (new Array(this.data.length)).fill(''),
                datasets: [{
                    label: 'My dataset',
                    backgroundColor: 'rgba(250,0,0)',
                    data: this.data
                }]
            }, {
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
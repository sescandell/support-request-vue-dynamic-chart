<template>
    <div class="card-item">
        <div class="graph">
            <bar-chart-item2 v-if="reactive" :data="itemDataset" />
            <bar-chart-item v-else  :data="itemDataset" />
        </div>
        <div class="infos">
            <ul>
                <li><label><input type="checkbox" v-model="reactive"/> ReactiveData</label></li>
                <li><strong>Name:</strong> {{item.name}}</li>
                <li><strong>Data length:</strong> {{item.data.length}}</li>
                <li><strong>Last data value:</strong> {{item.data[item.data.length-1]}}</li>
                <li><strong>Last update:</strong> {{item.lastUpdate.toLocaleString()}}</li>
            </ul>
        </div>
    </div>
</template>


<script>
    import BarChartItem from './BarChartItem.vue';
    import BarChartItem2 from './BarChartItem2.vue';

    export default {
        components: {
            BarChartItem,
            BarChartItem2
        },
        props: {
            item: {
                type: Object,
                required: true
            }
        },
        data() {
            return {
                reactive: false
            }
        },
        computed: {
            itemDataset() {
                return this.item.data;
            }
        }
    }
</script>

<style scoped>
    .card-item{
        width: 75%;
        margin: auto;
    }

    .graph {
        width: 65%;
        height: 105px;
        padding-bottom: 50px;
        display: inline-flex;
        position: relative;
    }

    .infos {
        display: inline-block;
        margin-left: 5%;
        width: 30%;
    }

    .infos li {
        text-align: left;
        list-style: none;
    }
</style>
<template>
  <div>
    <label><input type="checkbox" v-model="timerStarted" /> Start/Stop timer</label>
    <card-item v-for="item in items" :key="item.id" :item="item" />
  </div>
</template>

<script>
import CardItem from './CardItem.vue';

class Model {
    constructor(id, name, data) {
        this.id = id;
        this.name = name;
        this.data = data;
        this.lastUpdate = new Date();
    }
}

const itemList = [
  new Model(1, "item1", [5,4,17,3,9,8,5,4,17,3,9,8]),
  new Model(2, "item2", [6,8,1,2,3,4,6,8,1,2,3,4]),
  new Model(3, "item3", [1,2,7,3,3,0,1,2,7,3,3,0]),
];

let intervalHandler = null;
function startTimer() {
  intervalHandler = setInterval(function() {
    itemList[0].lastUpdate = new Date();
    itemList[0].data.push(Math.floor(Math.random()*10));
  }, 2000);
}

function stopTimer() {
  intervalHandler && clearInterval(intervalHandler);

  intervalHandler = null;
}

export default {
  components: {
    CardItem
  },
  data() {
    return {
      items: itemList,
      timerStarted: false
    };
  },
  watch: {
    timerStarted: function(newValue) {
      if (!!newValue) {
        startTimer();
      } else {
        stopTimer();
      }
    }
  }
}
</script>


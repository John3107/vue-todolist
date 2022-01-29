<template>
    <div class="memory-plot">
        <div class="plot" :style="{background: `conic-gradient(#999 0% ${freeMemoryPercent}%, #000 ${freeMemoryPercent}% 100%)`}"></div>
     </div>
</template>

<script>
export default {
name: "Plot",
data(){
return{
memoryAll: "50 GB",
memoryReserved: "7 GB",
}
},
  computed: {
    freeMemoryPercent() {
      let memoryAll = +this.memoryAll.split(' ')[0]
      let memoryReserved = +this.memoryReserved.split(' ')[0]
      let difference = memoryAll - memoryReserved
      let result = difference / (memoryAll / 100)
      return result
    }
  },
}
</script>

<style>
      .memory-plot {
        display: flex;
        align-items: center;
      }
        .plot {
          border-radius: 50%;
          width: 36px;
          height: 36px;
        }
      
</style>
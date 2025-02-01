<template>
  <div id="app">
    <header>
      <h1>Project Timeline</h1>
    </header>
    <main>
      <GanttChart />
    </main>
  </div>
</template>

<script>
import GanttChart from './components/GanttChart.vue'

export default {
  name: 'App',
  components: {
    GanttChart
  }
}
</script>

<style>
#app {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
    Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin: 0;
  padding: 0;
  min-height: 100vh;
  background-color: #f8fafc;
}

header {
  background-color: #fff;
  padding: 1rem 2rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

h1 {
  margin: 0;
  font-size: 1.5rem;
  color: #1e293b;
}

main {
  padding: 2rem;
}
</style>

<template>
  <div class="gantt-container">
    <div class="gantt-chart" ref="ganttContainer"></div>
  </div>
</template>

<script>
import Gantt from 'frappe-gantt'

export default {
  name: 'GanttChart',
  data() {
    return {
      ganttChart: null,
      tasks: [
        {
          id: 'Task 1',
          name: 'Design Phase',
          start: '2024-03-01',
          end: '2024-03-05',
          progress: 85,
          dependencies: ''
        },
        {
          id: 'Task 2',
          name: 'Development Phase',
          start: '2024-03-06',
          end: '2024-03-15',
          progress: 60,
          dependencies: 'Task 1'
        },
        {
          id: 'Task 3',
          name: 'Testing Phase',
          start: '2024-03-16',
          end: '2024-03-20',
          progress: 30,
          dependencies: 'Task 2'
        }
      ]
    }
  },
  mounted() {
    this.initGantt()
  },
  methods: {
    initGantt() {
      this.ganttChart = new Gantt(this.$refs.ganttContainer, this.tasks, {
        header_height: 50,
        column_width: 30,
        step: 24,
        view_modes: ['Day', 'Week', 'Month'],
        bar_height: 20,
        bar_corner_radius: 3,
        arrow_curve: 5,
        padding: 18,
        view_mode: 'Month',
        date_format: 'YYYY-MM-DD',
        custom_popup_html: null
      })

      this.ganttChart.change_view_mode('Month')
    },
    changeViewMode(mode) {
      if (this.ganttChart) {
        this.ganttChart.change_view_mode(mode)
      }
    }
  }
}
</script>

<style scoped>
.gantt-container {
  margin: 20px;
  padding: 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.gantt-chart {
  width: 100%;
  height: 100%;
}

/* Frappe Gantt custom styles */
:deep(.gantt) {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}

:deep(.bar-progress) {
  fill: #a3a3ff;
}

:deep(.bar) {
  fill: #b8c2cc;
}

:deep(.grid-header) {
  fill: #f9fafb;
  stroke: #e2e8f0;
}

:deep(.grid-row) {
  fill: #ffffff;
}

:deep(.lower-text, .upper-text) {
  font-size: 12px;
  fill: #64748b;
}

:deep(.today-highlight) {
  fill: #fcf8e3;
  opacity: 0.5;
}
</style> 
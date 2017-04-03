<script>
import TableNormal from './TableNormal.vue'

export default {
  render (h) {
    var defaultScopedSlots = {
      'date': props => h('span', (new Date(props.value)).toLocaleDateString())
    }
    return h('table-normal', {
      props: {
        columns: this.columns,
        data: this.data,
        rowsByColumn: this.rowsByColumn
      },
      scopedSlots: Object.assign(defaultScopedSlots, this.$scopedSlots)
    })
  },
  name: 'app',
  data () {
    return {
      columns: ['title', 'date'],
      data: [
        { title: 'Testentry #1', date: new Date() },
        { title: 'Testentry #2', date: new Date() },
        { title: 'Testentry #3', date: new Date() }
      ]
    }
  },
  components: {
    TableNormal
  },
  computed: {
    rowsByColumn () {
      // Transposes rows and columns
      var rowsByColumn = {}
      for (let i = this.columns.length; i--;) {
        var column = this.columns[i]
        rowsByColumn[column] = []
        for (let i = this.data.length; i--;) {
          rowsByColumn[column].push(this.data[i][column])
        }
      }
      return rowsByColumn
    }
  }
}
</script>

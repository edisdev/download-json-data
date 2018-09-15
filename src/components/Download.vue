<template>
  <a class="download-button"
     :href="convertData"
     :download="`${fileName}.${fileType}`">
     {{ ButtonText }}
  </a>
</template>

<script>
export default {
  name: 'DownloadButton',
  props: {
    fileName: {
      type: String,
      required: true
    },
    downloadData: {
      type: Array,
      required: true
    },
    fileType: {
      type: String,
      required: true
    },
    DataTitles: {
      type: Array,
      default () {
        return []
      }
    },
    ButtonText: {
      type: String,
      required: true
    }
  },
  computed: {
    convertData () {
      let contentType = ''
      let dData = ''
      let blob
      let url
      let titles
      switch (this.fileType) {
        case 'json':
          contentType = 'application/json'
          dData = JSON.stringify(this.downloadData, null, 2)
          blob = new Blob([dData], { type: contentType })
          url = window.URL.createObjectURL(blob)
          break

        case 'csv':
          dData += 'data:text/csv;sep=;charset=utf-8,%EF%BB%BF'
          titles = this.DataTitles.join(',')
          dData += titles + '\r\n'
          this.downloadData.map(item => {
            const keys = Object.keys(item)
            keys.forEach((key, index) => {
              dData += item[key]
              if (keys.length > index) {
                dData += ','
              }
            })
            dData += '\r\n'
          })
          url = dData

          break

        case 'xls':
          contentType = 'application/xml'

          titles = this.DataTitles.join(',')
          dData += titles + '\r\n'
          this.downloadData.map(item => {
            const keys = Object.keys(item)
            keys.forEach((key, index) => {
              dData += item[key]
              if (keys.length > index) {
                dData += ','
              }
            })
            dData += '\r\n'
          })
          blob = new Blob([dData], { type: contentType })
          url = window.URL.createObjectURL(blob)
          break
        default:
          break
      }
      return url
    }
  }
}
</script>

<style>
.download-button {
  display: flex;
  min-width: 46px;
  max-width: 320px;
  min-height: 46px;
  border-radius: 3px;
  align-items: center;
  justify-content: center;
  border: none;
  text-decoration: none;
  color: inherit;
}
</style>

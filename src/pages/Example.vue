<template>
  <section>
    <!-- FOR XLS FİLE -->
  <Download :download-data="periodicTable"
            file-type="xls"
            file-name="Periyodik Tablo - Bazı Elementler"
            :data-titles="titles"
            class="periodic_table color-1"
            button-text="Download Period Table As Excel"/>
  <!-- FOR CSV FİLE  -->
    <Download :download-data="periodicTable"
            file-type="csv"
            file-name="Periyodik Tablo - Bazı Elementler"
            :data-titles="titles"
            class="periodic_table color-2"
            button-text="Download Period Table As CSV"/>
    <!-- FOR JSON FİLE -->
    <Download :download-data="periodicTable"
            file-type="json"
            file-name="Periyodik Tablo - Bazı Elementler"
            class="periodic_table color-3"
            button-text="Download Period Table As JSON"/>
    <div class="datas">
      <textarea v-model="code" @change="changeData" class="editor"></textarea>
      <div class="code-field">
        <h4>DATA</h4>
        <hr>
        <code class="json">
        {{ periodicTable }}
      </code>
      </div>
    </div>
  </section>
</template>
<script>
import Download from '@/components/Download'

export default {
  name: 'Home',
  components: {
    Download
  },
  data () {
    return {
      code: null,
      periodicTable: [],
      elements: [
        {
          name: 'Helyum',
          symbol:
            'He',
          category:
            'SoyGaz'
        },
        {
          name: 'Oksijen',
          symbol:
            'O',
          category:
            'Ametal'
        },
        {
          name: 'Magnezyum',
          symbol:
            'Mg',
          category:
            'Metal'
        }

      ],
      titles: [
        'Element Adı',
        'Sembol',
        'Türü'
      ]
    }
  },
  created () {
    this.code = JSON.stringify(this.elements, null, 2)
    this.periodicTable = JSON.parse(this.code)
  },
  methods: {
    changeData () {
      this.periodicTable = JSON.parse(this.code)
    }
  }
}
</script>

<style>
  section {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    padding: 10px;
  }
 .periodic_table {
    color: #fff !important;
    font-weight: bold;
    font-size: 15px;
    flex: 1;
  }
  .datas {
    width: 100vw;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 40px;
  }
  .datas .code-field {
    width: 40%;
    margin-top: 20px;
    margin-left: 8px;
  }
  .periodic_table + .periodic_table {
    margin-left: 7px;
  }
  .periodic_table.color-1 {
    background: #00942d;
  }

   .periodic_table.color-2 {
     background: rgb(0, 206, 188);
  }

   .periodic_table.color-3 {
     background: rgb(234, 190, 8);
  }

  .datas .editor {
    max-width: 400px;
    width: 100%;
    min-height: 220px;
    height: 100%;
    border-radius: 3px;
    background: #000;
    color: greenyellow;
    padding: 20px;
    border: 0;
    resize: none;
    overflow: scroll;
    font-size: 14px;
  }
  .editor:focus {
    outline: 0;
    border: 1px solid greenyellow;
  }

  @media screen and (max-width: 750px){
    .periodic_table {
      width: 100px;
    }
    .datas .editor {
      max-width: 200px;
      min-height: 200px;
    }
  }
</style>

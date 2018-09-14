<template>
  <section>
    <!-- FOR XLS FİLE -->
  <Download :download-data="periodic_table"
            file-type="xls"
            file-name="Periyodik Tablo - Bazı Elementler"
            :data-titles="titles"
            class="periodic_table color-1"
            button-text="Download Period Table As Excel"/>
  <!-- FOR CSV FİLE  -->
    <Download :download-data="periodic_table"
            file-type="csv"
            file-name="Periyodik Tablo - Bazı Elementler"
            :data-titles="titles"
            class="periodic_table color-2"
            button-text="Download Period Table As CSV"/>
    <!-- FOR JSON FİLE -->
    <Download :download-data="periodic_table"
            file-type="json"
            file-name="Periyodik Tablo - Bazı Elementler"
            class="periodic_table color-3"
            button-text="Download Period Table As JSON"/>
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
      periodic_table: [
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
  }
}
</script>

<style>
  section {
    display: flex;
    justify-content: center;
  }
 .periodic_table {
    color: #fff !important;
    font-weight: bold;
    font-size: 15px;
    flex: 1;
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
</style>

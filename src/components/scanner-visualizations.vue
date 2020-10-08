<template>
  <div>
    <div>
      <h5>Distribución de los resultados:</h5>

      <div class="o-grid">
        <div class="o-grid__col u-12 u-padding-bottom-4">
          <ScannerLegend :result="result" :styles="styles"></ScannerLegend>
        </div>
        <div class="o-grid__col u-12 u-6@sm">
          <ScannerSunburst :result="result" :styles="styles"></ScannerSunburst>
          <tipi-message type="info" icon>
              Resultados sobre la distribución de los ODS, sus metas correspondientes y los términos de cada meta.<br/>
              Puedes hacer zoom haciendo click en cada una de las porciones.
          </tipi-message>
        </div>
        <div class="o-grid__col u-12 u-6@sm u-text-center">
          <ScannerWordsCloud :result="result" :maxResults="tagsInWordCloud" :styles="styles"></ScannerWordsCloud>
          <tipi-message type="info" icon>Se muestran un máximo de {{tagsInWordCloud}} etiquetas</tipi-message>
        </div>
      </div>
    </div>
    <div class="u-padding-top-10">
      <h5>Compara los resultados:</h5>
      <tipi-message type="info" icon>Selecciona un texto de referencia para poder comparar tus resultados con él.</tipi-message>
      <div class="c-select-label u-block">
        <label for="topic">Comparar con...</label>
        <multiselect
          v-model="textToCompare"
          :options="preScannedTexts.map(pst => pst.title)"
          name="pre-scanned-text" id="pre-scanned-text" placeholder="Selecciona uno">
        </multiselect>
      </div>
      <ScannerBarchart :result="this.result" :resultToCompare="resultToCompare" :styles="styles"></ScannerBarchart>
    </div>

    <div class="u-padding-top-10">
      <h5>Resultados en detalle:</h5>
      <p v-if="result.topics.length>9">Se muestran solo 10 resultados de {{result.topics.length}}, para ver el resto descárgate el archivo.</p>
      <p v-if="result.topics.length<9">También puedes guardarte los datos descargándote el archivo.</p>
      <ScannerTable :result="result"></ScannerTable>
    </div>

    <div class="o-grid__col u-12 u-margin-top-4">
      <export-excel
        :data="csvItems"
        class="c-button c-button--icon-right c-button--primary"
      >
        Descarga tus resultados
        <span class="c-icon c-icon--type-download"><svg xmlns="http://www.w3.org/2000/svg" width="12" height="16" fill="none" viewBox="0 0 12 16"><path fill="#2D4252" d="M12 5.647H8.571V0H3.43v5.647H0l6 6.588 6-6.588zm-12 8.47V16h12v-1.882H0z"></path></svg></span>
      </export-excel>
      <tipi-message type="info" icon>Los resultados se descargarán en formato excel.</tipi-message>
    </div>
  </div>
</template>

<script>
import { TipiMessage, TipiCsvDownload } from 'tipi-uikit';
import ScannerWordsCloud from '@/components/scanner-wordscloud.vue';
import ScannerSunburst from '@/components/scanner-sunburst.vue';
import ScannerBarchart from '@/components/scanner-barchart.vue';
import ScannerTable from '@/components/scanner-table.vue';
import ScannerLegend from '@/components/scanner-legend.vue';
import Multiselect from 'vue-multiselect';
import preScannedTexts from '@/scanned';
import config from '@/config';
import Vue from 'vue'
import excel from 'vue-excel-export'

Vue.use(excel)

export default {
  name: "ScannerVisualizations",
  components: {
    TipiMessage,
    TipiCsvDownload,
    ScannerWordsCloud,
    ScannerSunburst,
    ScannerBarchart,
    ScannerTable,
    ScannerLegend,
    Multiselect,
  },
  props: {
    result: {
      type: Object || null,
      required: true,
    }
  },
  data() {
    return {
      preScannedTexts: preScannedTexts,
      resultToCompare: null,
      textToCompare: null,
      csvItems: this.result.tags,
      scanned: {},
      tagsInWordCloud: 25,
      styles: config.STYLES,
    };
  },
  watch: {
    textToCompare(val) {
      const compareWith = preScannedTexts.filter(d => d.title === val);
      this.resultToCompare = compareWith.length
        ? compareWith[0]
        : null;
    }
  }
}
</script>

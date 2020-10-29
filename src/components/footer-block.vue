<template>
  <div>
    <div id="footer" class="o-container o-container--fluid o-section u-bg-secondary-light">

      <div class="o-container">
        <div class="o-grid">
          <div class="o-grid__col u-7@sm u-margin-top-4">
            <p class="u-text-overline">Impulsado por</p>
            <div class="o-grid">
              <div class="o-grid__col u-7@sm">
                <a href="https://www.observatorisocial.ad/" target="_blank"><img src="/img/logo-observatori-color.jpg" class="big" alt="Logo de l'Observatori Social d'Andorra"></a>
              </div>
              <div class="o-grid__col u-5@sm">
                <a href="https://www.iea.ad/" target="_blank"><img src="/img/logo-IEA-color.jpg" class="big" alt="Logo de l'Institut d'Estudis Andorrans"></a>
              </div>
              <div class="o-grid__col u-7@sm">
                <a href="http://www.consellgeneral.ad/" target="_blank"><img src="/img/logo-consellgeneral-color.jpg" class="big" alt="Logo del Consell General del Principat d'Andorra"></a>
              </div>
              <div class="o-grid__col u-5@sm">
                <a href="https://www.govern.ad/" target="_blank"><img src="/img/logo-governandorra-color.jpg" class="big" alt="Logo del Govern d'Andorra"></a>
              </div>
              <div class="o-grid__col u-7@sm">
                <a href="https://www.actua.ad/" target="_blank"><img src="/img/logo-actua-color.jpg" class="big" alt="Logo de la Iniciativa Actua"></a>
              </div>
              <div class="o-grid__col u-5@sm">
                <a href="http://politicalwatch.es" target="_blank"><img src="/img/ciecode.png" class="big" alt="Logo de CIECODE"></a>
              </div>
            </div>
          </div>
          <div class="o-grid__col u-4@sm u-offset-1@sm u-margin-top-4">
            <p class="u-text-overline">Contacto</p>
            <tipi-icon icon="github" class="c-icon--secondary-dark" />&nbsp;<a class="u-color-secondary-dark u-text-tbody2" href="http://github.com/politicalwatch/" title="github.com/politicalwatch" target="_blank">Consulta nuestro código en Github</a>
            <br>
            <tipi-icon icon="mail" class="c-icon--secondary-dark" />&nbsp;<a class="u-color-secondary-dark u-text-tbody2" href="mailto:parlamento2030@ciecode.es" title="parlamento2030@ciecode.es" target="_blank">Escribe a parlamento2030@ciecode.es</a>
          </div>
        </div>
        <div class="o-grid">
          <div class="o-grid__col u-12@sm u-margin-top-4">
            <p class="u-color-secondary-dark u-text-tbody2">{{ (new Date()).getFullYear() }} Political Watch. Algunos derechos reservados.</p>
          </div>
        </div>
      </div>

    </div>

    <div class="c-decorator" style="background-image: url('/img/multicolor.jpg')"></div>

    <cookie-law theme="base" buttonText="Entendido" buttonClass="c-button c-button--primary" message="Este sitio usa cookies para asegurarte la mejor experiencia web."></cookie-law>

  </div>
</template>

<script>
  import CookieLaw from 'vue-cookie-law';
  import { TipiIcon } from 'tipi-uikit';

  export default {
    name: "footer-block",
    components: {
      CookieLaw,
      TipiIcon
    }
  }
</script>

<style scoped lang="scss">
</style>

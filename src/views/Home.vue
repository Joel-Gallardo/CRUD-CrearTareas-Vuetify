<template>
  <div>

    <v-container>
      <v-row>
        <v-col xs="12" sm="6">
          <v-card>
            <v-img
              src="https://besthqwallpapers.com/Uploads/23-5-2018/53677/thumb2-max-verstappen-f1-4k-raceway-rb14.jpg">
              <v-container>
                <v-row>
                  <v-col>
                    <span class="white--text">Red Bull F1 RB16</span>
                  </v-col>
                </v-row>
              </v-container>
            </v-img>
            <v-card-title>
              Reb Bull Racing F1
            </v-card-title>
            <v-card-text>
              Red Bull Racing es una escudería austriaca de Fórmula 1 con base en Milton Keynes propiedad de la empresa
              de bebidas energéticas Red Bull
            </v-card-text>
            <v-card-actions>
              <v-btn @click="dialogrb16 = true" color="orange lighten-2">
                Mas Info
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>

        <v-col xs="12" sm="6">
          <v-card>
            <v-img
              src="https://besthqwallpapers.com/Uploads/12-3-2019/83013/thumb2-valtteri-bottas-4k-mercedes-w10-f1-raceway-2019-f1-cars.jpg">
              <v-container>
                <v-row>
                  <v-col>
                    <span class="white--text">Mercedes AMG F1 W11</span>
                  </v-col>
                </v-row>
              </v-container>
            </v-img>
            <v-card-title>
              Mercedes AMG Petronas Motorsport F1
            </v-card-title>
            <v-card-text>
              Mercedes-Benz es una de las automotrices más exitosas de la Fórmula 1, considerada uno de los cuatros
              equipos con mejores resultados
            </v-card-text>
            <v-card-actions>
              <v-btn color="info" @click="dialogw11 = true">Mas Info</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>

      <!-- Dialog -->

      <v-dialog v-model="dialogrb16" width="500" persistent>
        <v-card>
          <v-card-title>RB16</v-card-title>
          <v-card-text>El Red Bull RB16 es un monoplaza de Fórmula 1 diseñado por Red Bull Racing para competir en la
            temporada 2020.
            <br><br>
            Volverá a ser utilizado en la temporada 2021 bajo el nombre de Red Bull RB16B,​ y será conducido por Sergio
            Pérez y Max Verstappen. Además será el último monoplaza motorizado por Honda. El chasis fue presentado
            el 23 de febrero de 2021 en línea</v-card-text>
          <v-divider></v-divider>
          <v-card-actions>
            <v-btn @click="dialogrb16 = false">Cerrar</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>

      <v-dialog v-model="dialogw11" width="500" persistent>
        <v-card>
          <v-card-title>W11</v-card-title>
          <v-card-text>El Mercedes-AMG F1 W11 EQ Performance es un monoplaza diseñado por Mercedes-AMG Petronas Formula
            One Team para competir en la temporada 2020 de Fórmula 1 y fue presentado el 14 de febrero en el Circuito de
            Silverstone.
            <br><br>
            El coche es conducido por el campeón defensor Lewis Hamilton y el finlandés Valtteri Bottas.​ George
            Russell, piloto de Williams, sustituyó a Hamilton en la anteúltima carrera del campeonato tras el positivo
            de COVID-19 del británico.</v-card-text>
          <v-divider></v-divider>
          <v-card-actions>
            <v-btn @click="dialogw11 = false">Cerrar</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>

      <!-- Fin Dialog -->

    </v-container>



  </div>
</template>

<script>
  export default {
    name: 'Home',
    data() {
      return {
        dialogrb16: false,
        dialogw11: false
      }
    }
  }
</script>

<template>
  <div class="nutrition">
    <div id="nutritionfacts">
      <table cellspacing="0" cellpadding="0">
        <tbody>
          <tr>
            <td align="center" class="header">Nutrition Facts</td>
          </tr>
          <tr>
            <td align="center">Yield</td>
            <div class="weight">{{ itemYield }}</div>
          </tr>
          <tr style="height: 7px">
            <td bgcolor="#000000"></td>
          </tr>
          <tr>
            <td style="font-size: 7pt">
              <div class="line">Amount Per Serving</div>
            </td>
          </tr>
          <tr>
            <td>
              <div class="line">
                <div class="label">
                  Calories
                  <div class="weight">{{calories}}</div>
                </div>
                <div style="padding-top: 1px; float: right;" class="labellight">
                  Calories From Fat
                  <div class="weight">{{n(caloriesFromFat)}}</div>
                </div>
              </div>
            </td>
          </tr>
          <tr>
            <td>
              <div class="line">
                <div class="dvlabel">
                  % Daily Value
                  <sup>*</sup>
                </div>
              </div>
            </td>
          </tr>
          <tr>
            <td>
              <div class="line">
                <div class="label">
                  Total Fat
                  <div class="weight">{{n(totalFatInGrams.quantity)}}{{totalFatInGrams.unit}}</div>
                </div>
                <div class="dv">{{n(totalFatPercentage.quantity)}}{{totalFatPercentage.unit}}</div>
              </div>
            </td>
          </tr>
          <tr>
            <td class="indent">
              <div class="line">
                <div class="labellight">
                  Saturated Fat
                  <div
                    class="weight"
                  >{{n(saturatedFatInGrams.quantity)}}{{saturatedFatInGrams.unit}}</div>
                </div>
                <div
                  class="dv"
                >{{n(saturatedFatPercentage.quantity)}}{{saturatedFatPercentage.unit}}</div>
              </div>
            </td>
          </tr>
          <tr>
            <td class="indent">
              <div class="line">
                <div class="labellight">
                  <i>Trans</i> Fat
                  <div class="weight">
                    {{n(transFatInGrams.quantity)}}{{transFatInGrams.unit}}
                    <div></div>
                  </div>
                </div>
              </div>
            </td>
          </tr>
          <tr>
            <td>
              <div class="line">
                <div class="label">
                  Cholesterol
                  <div class="weight">{{n(cholesterolInGrams.quantity)}}{{cholesterolInGrams.unit}}</div>
                </div>
                <div class="dv">{{n(cholesterolPercentage.quantity)}}{{cholesterolPercentage.unit}}</div>
              </div>
            </td>
          </tr>
          <tr>
            <td>
              <div class="line">
                <div class="label">
                  Sodium
                  <div class="weight">{{n(sodiumInGrams.quantity)}}{{sodiumInGrams.unit}}</div>
                </div>
                <div class="dv">{{n(sodiumPercentage.quantity)}}{{sodiumPercentage.unit}}</div>
              </div>
            </td>
          </tr>
          <tr>
            <td>
              <div class="line">
                <div class="label">
                  Total Carbohydrates
                  <div class="weight">{{n(totalCarbsInGrams.quantity)}}{{totalCarbsInGrams.unit}}</div>
                </div>
                <div class="dv">{{n(totalCarbsPercentage.quantity)}}{{totalCarbsPercentage.unit}}</div>
              </div>
            </td>
          </tr>
          <tr>
            <td class="indent">
              <div class="line">
                <div class="labellight">
                  Dietary Fiber
                  <div class="weight">{{n(fiberInGrams.quantity)}}{{fiberInGrams.unit}}</div>
                </div>
                <div class="dv">{{n(fiberInGrams.quantity)}}{{fiberInGrams.unit}}</div>
              </div>
            </td>
          </tr>
          <tr>
            <td class="indent">
              <div class="line">
                <div class="labellight">
                  Sugars
                  <div class="weight">{{n(sugarsInGrams.quantity)}}{{sugarsInGrams.unit}}</div>
                </div>
              </div>
            </td>
          </tr>
          <tr>
            <td>
              <div class="line">
                <div class="label">
                  Protein
                  <div class="weight">{{n(proteinInGrams.quantity)}}{{proteinInGrams.unit}}</div>
                </div>
              </div>
            </td>
          </tr>
          <tr style="height: 7px">
            <td bgcolor="#000000"></td>
          </tr>
          <tr>
            <td>
              <table cellspacing="0" cellpadding="0" border="0" class="vitamins">
                <tbody>
                  <tr>
                    <td>Vitamin A &nbsp;&nbsp; {{n(vitaminAPercentage.quantity)}}{{vitaminAPercentage.unit}}</td>
                    <td align="center">•</td>
                    <td
                      align="right"
                    >Calcium &nbsp;&nbsp; {{n(calciumPercentage.quantity)}}{{calciumPercentage.unit}}</td>
                  </tr>
                  <tr>
                    <td>Vitamin C &nbsp;&nbsp; {{n(vitaminCPercentage.quantity)}}{{vitaminCPercentage.unit}}</td>
                    <td align="center">•</td>
                    <td
                      align="right"
                    >Iron &nbsp;&nbsp; {{n(ironPercentage.quantity)}}{{ironPercentage.unit}}</td>
                  </tr>
                  <tr>
                    <td>Vitamin D &nbsp;&nbsp; {{n(vitaminDPercentage.quantity)}}{{vitaminDPercentage.unit}}</td>
                    <td align="center">•</td>
                    <td
                      align="right"
                    >Potassium &nbsp;&nbsp; {{n(potassiumPercentage.quantity)}}{{potassiumPercentage.unit}}</td>
                  </tr>
                </tbody>
              </table>
            </td>
          </tr>
          <tr>
            <td>
              <div class="line">
                <div class="labellight">
                  * Based on a regular
                  <a href="#">2000 calorie diet</a>
                  <br />
                  <br />
                  <i>Nutritional details are an estimate and should only be used as a guide for approximation.</i>
                </div>
              </div>
            </td>
          </tr>
        </tbody>
      </table>
      <div id="edamam-badge" data-color="white" align="center"></div>
    </div>
  </div>
</template>

<script>
import photos from "@/assets/data/gallery.json";
import axios from "axios";

const YOUR_APP_KEY = "75219a3520300c64c07e474cc731a29b";
const YOUR_APP_ID = "8b0a6cf6";

export default {
  name: "Nutrition",
  data() {
    return {
      itemYield: 0,
      caloriesFromFat: 0,
      calories: 0,
      totalFatInGrams: 0,
      totalFatPercentage: 0,
      saturatedFatInGrams: 0,
      saturatedFatPercentage: 0,
      transFatInGrams: 0,
      cholesterolInGrams: 0,
      cholesterolPercentage: 0,
      sodiumInGrams: 0,
      sodiumPercentage: 0,
      totalCarbsInGrams: 0,
      totalCarbsPercentage: 0,
      fiberInGrams: 0,
      fiberPercentage: 0,
      sugarsInGrams: 0,
      proteinInGrams: 0,
      vitaminAPercentage: 0,
      vitaminCPercentage: 0,
      vitaminDPercentage: 0,
      calciumPercentage: 0,
      ironPercentage: 0,
      potassiumPercentage: 0
    };
  },
  methods: {
    n(x) {
      // format numbers to fixed.
      return x && x.toFixed(0);
    }
  },

  async created() {
    const nutritionResult = (await axios.post(
      `https://api.edamam.com/api/nutrition-details?app_id=${YOUR_APP_ID}&app_key=${YOUR_APP_KEY}`,
      {
        title: photos[this.$route.query.id].title,
        servingsYield: photos[this.$route.query.id].servingsYield,
        ingr: photos[this.$route.query.id].recipe.ingredients
      }
    )).data;
    this.itemYield = nutritionResult.yield;
    this.calories = nutritionResult.calories;
    this.caloriesFromFat = nutritionResult.totalNutrientsKCal.FAT_KCAL.quantity;
    this.totalFatInGrams = nutritionResult.totalNutrients.FAT;
    this.totalFatPercentage = nutritionResult.totalDaily.FAT;
    this.saturatedFatInGrams = nutritionResult.totalNutrients.FASAT;
    this.saturatedFatPercentage = nutritionResult.totalDaily.FASAT;
    this.transFatInGrams = nutritionResult.totalNutrients.FATRN;
    this.cholesterolInGrams = nutritionResult.totalNutrients.CHOLE;
    this.cholesterolPercentage = nutritionResult.totalDaily.CHOLE;
    this.sodiumInGrams = nutritionResult.totalNutrients.NA;
    this.sodiumPercentage = nutritionResult.totalDaily.NA;
    this.totalCarbsInGrams = nutritionResult.totalNutrients.CHOCDF;
    this.totalCarbsPercentage = nutritionResult.totalDaily.CHOCDF;
    this.fiberInGrams = nutritionResult.totalNutrients.FIBTG;
    this.fiberPercentage = nutritionResult.totalDaily.FIBTG;
    this.sugarsInGrams = nutritionResult.totalNutrients.SUGAR;
    this.proteinInGrams = nutritionResult.totalNutrients.PROCNT;
    this.vitaminAPercentage = nutritionResult.totalDaily.VITA_RAE;
    this.vitaminCPercentage = nutritionResult.totalDaily.VITC;
    this.vitaminDPercentage = nutritionResult.totalDaily.VITD;
    this.calciumPercentage = nutritionResult.totalDaily.CA;
    this.ironPercentage = nutritionResult.totalDaily.FE;
    this.potassiumPercentage = nutritionResult.totalDaily.K;
    return;
  }
};
</script>

<style lang='scss'>
@import "@/assets/styles/main.scss";

#nutritionfacts {
  background-color: white;
  border: 1px solid black;
  margin: 0 auto;
  padding: 0.5rem;
  width: 100%;
  td {
    color: black;
    font-family: "Arial Black", "Helvetica Bold", sans-serif;
    padding: 0;
    &.header {
      font-family: "Arial Black", "Helvetica Bold", sans-serif;
      font-size: 28px;
      white-space: nowrap;
    }
  }
  @include media-query(lg) {
    width: 50%;
  }

  div {
    &.label {
      float: left;
      font-family: "Arial Black", "Helvetica Bold", sans-serif;
    }
    &.serving {
      font-family: Arial, Helvetica, sans-serif;
      text-align: center;
    }
    &.weight {
      display: inline;
      font-family: Arial, Helvetica, sans-serif;
      /* padding-left: 1px; */
    }
    &.dv {
      display: inline;
      float: right;
      font-family: "Arial Black", "Helvetica Bold", sans-serif;
    }
  }
  table.vitamins td {
    font-family: Arial, Helvetica, sans-serif;
    white-space: nowrap;
    width: 33%;
  }
  div {
    &.line {
      border-top: 1px solid black;
    }
    &.labellight {
      float: left;
      font-family: Arial, Helvetica, sans-serif;
    }
  }
  .highlighted {
    border: 1px dotted grey;
    padding: 2px;
  }
}
</style>

<template>
  <div class="container overflow-y" id="form-image">
    <b-form @submit.prevent="submitData" @reset="reset">
      <b-form-group id="input-group-2" label="Your Quotes" label-for="input-2">
        <b-form-input id="input-2" v-model="form.quote" required ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-20" label="Author" label-for="input-20">
        <b-form-input id="input-20" v-model="form.author" required placeholder="Your name here"></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-4" label="Font Size" label-for="input-4">
        <b-form-input id="input-4" v-model="form.fontSize" required placeholder="Font Size"></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Quote Font" label-for="input-3">
        <b-form-select id="input-3" v-model="form.quoteFont" :options="fonts" required></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-5" label="Quote Font Color" label-for="input-5">
        <b-form-input type="color" id="input-5" v-model="form.quoteFontColor" required></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-9" label="Author Font" label-for="input-9">
        <b-form-select id="input-9" v-model="form.authorFont" :options="fonts" required></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-6" label="Author Font Color" label-for="input-6">
        <b-form-input type="color" id="input-6" v-model="form.authorFontColor" required></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-8" label="Allow Highlight" label-for="checkbox-1">
        <b-form-checkbox id="checkbox-1" v-model="form.enableHighlight" name="checkbox-1" value="1"></b-form-checkbox>
      </b-form-group>

      <b-form-group id="input-group-7" label="Highlight Color" label-for="input-7">
        <b-form-input type="color" id="input-7" v-model="form.highlightColor" required></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-10" label="Background Type" label-for="input-10">
        <b-form-select id="input-10" v-model="form.bgType" :options="types" required></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-11" label="Background Color" label-for="input-11">
        <b-form-input type="color" id="input-11" v-model="form.backgroundColor" required></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-15" label="Gradient Type" label-for="input-15">
        <b-form-select id="input-15" v-model="form.gradientType" :options="gradients" required></b-form-select>
      </b-form-group>

      <b-form-group id="input-group-12" label="Gradient Color 1" label-for="input-12">
        <b-form-input type="color" id="input-12" v-model="form.gradientColor1" required></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-13" label="Gradient Color 2" label-for="input-13">
        <b-form-input type="color" id="input-13" v-model="form.gradientColor2" required></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-14" label="Animation" label-for="input-14">
        <b-form-select id="input-14" v-model="form.animation" :options="animate" required></b-form-select>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "TextImage",
  data() {
    return {
      form: {
        quote: "",
        author: "",
        fontSize: "",
        quoteFont: null,
        quoteFontColor: "",
        authorFont: null,
        authorFontColor: "",
        enableHighlight: "0",
        highlightColor: "",
        bgType: "",
        backgroundColor: "",
        gradientType: "",
        gradientColor1: "",
        gradientColor2: "",
        animation: ""
      },
      fonts: [
        { text: "Select One", value: null },
        "AlegreyaSC",
        "ABeeZee",
        "AmaticSC",
        "Bangers",
        "BungeeShade",
        "ChelseaMarket",
        "Courgette",
        "DancingScript",
        "Lato Black",
        "LifeSavers",
        "Lora",
        "Montserrat",
        "PassionOne",
        "PlayfairDisplay",
        "SourceSansPro"
      ],
      types: [
        { text: "Solid", value: "solid" },
        { text: "Gradient", value: "gradient" }
      ],
      gradients: [
        { text: "Linear Gradient", value: "linear" },
        { text: "Radial Gradient", value: "radial" }
      ],
      animate: [
        { text: "None", value: "none" },
        { text: "Light Rays", value: "rays" },
        { text: "Glint", value: "glint" },
        { text: "Circles", value: "circle" }
      ]
    };
  },
  methods: {
    reset: function() {
        (this.quote = ""),
        (this.author = ""),
        (this.fontSize = ""),
        (this.quoteFont = null),
        (this.quoteFontColor = ""),
        (this.authorFont = null),
        (this.authorFontColor = ""),
        (this.enableHighlight = ""),
        (this.highlightColor = ""),
        (this.bgType = ""),
        (this.backgroundColor = ""),
        (this.gradientType = ""),
        (this.gradientColor1 = ""),
        (this.gradientColor2 = ""),
        (this.animation = "");
    },
    submitData: function() {
      let data = this.form;
      console.log(data);
      axios
        .post("http://35.192.129.227/image/transform", data)
        .then(({ data }) => {
          console.log(data);
          return this.$emit("image-link", data.url);
        })
        .catch(err => {
          // eslint-disable-next-line-no console
          console.log(err);
        });
    }
  },
  props: ['textResult'],
  watch: {
    textResult: function(n, o) {
      console.log(o)
      this.form.quote = n
    }
  }
};
</script>

<style lang="css" scoped>
  .container {
    padding: 20px;
    background-color:  rgba(34, 47, 62,0.5);
    color: white; 
    margin-top: 40px;
    margin-bottom: 80px;
  }
</style>
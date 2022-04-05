<template>
<div class="row row-cols-1 row-cols-md-2 row-cols-lg-3"  id="tablazat">
<div class="col" v-for="vizsgaidopont in vizsgaidopontok" v-bind:key="vizsgaidopont.id">
  <div class="card">
  <div class="card-body">
    <h5 class="card-title">{{ vizsgaidopont.targy }}</h5>
    <img v-if="vizsgaidopont.tipus == 'erettsegi'" src="@/assets/macska.jpg"/>
    <img v-if="vizsgaidopont.tipus == 'szakmai'" src="@/assets/kutya.jpg"/>
    <p class="card-text">{{vizsgaidopont.tipus}}</p>
    <p class="card-text">{{vizsgaidopont.kezdes}}</p>
  </div>
  </div>
</div>
</div>
</template>

<script>
export default {
  data () {
    return {
      vizsgaidopont:
      {
        id: null,
        targy: '',
        tipus: '',
        kezdes: null
      },
      vizsgaidopontok: []
    }
  },
  methods: {
    async vizsgaidopontokBetoltese () {
      let Response = await fetch('http://127.0.0.1:8000/api/vizsgaidopontok')
      let adat = await Response.json()
      this.vizsgaidopontok = adat
    }
  },
  mounted () {
    this.vizsgaidopontokBetoltese()
  }

}
</script>

<style>
img {
  width: 100%;
  height: 80%;
}
</style>

<template>
<div id="form" class="form-label">
<div>
  Tárgy: <input type="text" class="form-control" v-model="vizsgaidopont.targy">
</div>
<div>
  Típus:
  <select class="form-control" v-model="vizsgaidopont.tipus">
    <option value="szakmai">Szakmai</option>
    <option value="erettsegi">Érettsegi</option>
  </select>
</div>
<div>
  Kezdés: <input type="date" class="form-control" v-model="vizsgaidopont.kezdes">
</div>
<div>
  <input type="submit" @click="newVizsgaidopont()" value="Új vizsgaidőpont" class="form-control">
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
      }
    }
  },
  methods: {
    async newVizsgaidopont () {
      await fetch('http://127.0.0.1:8000/api/vizsgaidopontok', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'Accept': 'application/json'
        },
        body: JSON.stringify(this.vizsgaidopont)
      })
      await this.vizsgaidopontokBetoltese()
    },
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

</style>

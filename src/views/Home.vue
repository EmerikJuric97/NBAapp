<template>
<v-container>
  <v-row class="justify-center">
    <v-col cols="12">
      <v-parallax src="https://wallpaperaccess.com/full/128139.jpg"><h1 class="text-center jedan" style="color:white"><strong>UPOZNAJTE</strong> NBA</h1></v-parallax></v-col>
      <v-col cols="12" xs="12" sm="8" md="8" lg="8">
            <v-toolbar
    dark
    color="red darken-4"
  >
    <v-toolbar-title class="mx-2">Pretraži tim</v-toolbar-title>
    <v-autocomplete
      :items="slike"
      v-model="search"
      dense
      filled
      cache-items
      class="mx-auto"
      flat
      hide-no-data
      hide-details
      solo-inverted
      @input="odredenitim2(slike)"
    ></v-autocomplete>
  </v-toolbar>
  </v-col>
          
          </v-row>
<v-row>
  <v-col v-for="slika in slike" :key="slika" cols="lg-2 md-4">
  <v-card
    class="mx-auto my-12 moja"
    max-width="200"
  >

    <v-img
      height="20vh"
      width="210vh"
      class="slik image-fit justify-center"
      v-bind:src="slika.path"
      contain
    ></v-img>






      <v-dialog
        transition="dialog-top-transition"
        max-width="1500"
      >
        <template v-slot:activator="{ on, attrs }">

      <v-btn @click="odredenitim(slika.text)" class="justify-center" v-bind="attrs" v-on="on">{{slika.text}}</v-btn></template>
      <template v-slot:default="dialog">
          <v-card>
            <v-toolbar
              color="primary"
              dark
            >Igrači</v-toolbar>
            <v-card-text>
              <v-row>
                <v-col v-for="tim in timovi" :key="tim">
                  <v-card
    class="mx-auto my-12"
    max-width="374"
  >


    <v-img
      height="250"
      src="https://cdn.vuetifyjs.com/images/cards/cooking.png"
    ></v-img>

    <v-card-title class="justify-center">{{tim.name}}</v-card-title>

  
  </v-card>
                </v-col>
              </v-row>
            </v-card-text>
            <v-card-actions class="justify-end">
              <v-btn
                text
                @click="dialog.value = false"
              >Zatvori</v-btn>
            </v-card-actions>
          </v-card>
        </template>
      </v-dialog>











  </v-card>
  </v-col>
</v-row>



</v-container>
</template>

<script>
  export default {
    data: () => ({ 
      igraci: [],
      timovi: [],
      page: 1,
      totalPages: 0,
      search: '',
              headers: [
          {
            text: 'Dessert (100g serving)',
            align: 'start',
            sortable: false,
            value: 'name',
          }],
      slike: [{text:"gsw", path:"slike/gsw.png"},{text:"lac", path:"slike/lac.png"},{text:"lal", path:"slike/lal.png"},{text:"pho", path:"slike/pho.png"},
      {text:"sac", path:"slike/sac.png"},{text:"dal", path:"slike/dal.png"},{text:"hou", path:"slike/hou.png"},{text:"mem", path:"slike/mem.png"},{text:"nor", path:"slike/nor.png"},
      {text:"sas", path:"slike/sas.png"},{text:"den", path:"slike/den.png"},{text:"min", path:"slike/min.png"},{text:"okc", path:"okc.gif"},{text:"por", path:"slike/por.png"},
      {text:"uth", path:"slike/uth.png"},{text:"bos", path:"slike/bos.png"},{text:"bro", path:"slike/bro.png"},{text:"nyk", path:"slike/nyk.png"},{text:"phi", path:"slike/phi.png"},
      {text:"tor", path:"slike/tor.png"},{text:"chi", path:"slike/chi.png"},{text:"cle", path:"slike/cle.png"},{text:"det", path:"det.gif"},{text:"ind", path:"slike/ind.png"},
      {text:"mil", path:"slike/mil.png"},{text:"atl", path:"slike/atl.png"},{text:"cha", path:"slike/cha.png"},{text:"mia", path:"slike/mia.png"},{text:"orl", path:"slike/orl.png"},
      {text:"was", path:"slike/was.png"}],
      }),
      methods: {
        svitimovi: function() {
          this.axios.get('https://nba-players.herokuapp.com/teams').then((response) => {
            console.log(response.data)
            this.timovi = response.data
          })
        },
        odredenitim: function(imetima) {
          this.axios.get('https://nba-players.herokuapp.com/players-stats-teams/' + imetima).then((response) => {
            console.log(response.data)
            this.timovi = response.data
          })
        },
        odredenitim2: function() {
          this.axios.get('https://nba-players.herokuapp.com/players-stats-teams/' + this.search).then((response) => {
            console.log(response.data)
            this.timovi = response.data
          })
        },
      }
  }
</script>

<style scoped>
.moja {
 transition: 1s ease-in-out;
}

.moja:hover {
 transform: scale(1.1);
}

.naslov{
  justify-content: center;
  padding: auto;
  }
.jedan{
    font-size: 50px;
  }
</style>
<template>

<div>
    <b-row
     cols-lg="6"
     class="mb-2 mt-2">
        <b-form>
            <b-form-input
            placeholder="Pesquise pelo nome"
            v-model="search"
            />
        </b-form>
        <b-form-select
            v-model="selected"
            :options="options"
            />   
    </b-row>
   <b-row>
    <div 
    class="col-md-3"
    v-for="(digimon, index) in itemsFiltered"
    :key="index">
        <b-card
            :title="digimon.name"
            :img-src="digimon.img"
            img-alt="Digimon Image"
            img-top
            tag="article"
            style="max-width: 20rem;"
            class="mb-2"
        >
            <b-button  
            :variant="digimon.lvl === 'In Training' ? 'primary' : digimon.lvl ==='Rookie' ? 'secondary' : digimon.lvl === 'Champion' ? 'success' : digimon.lvl === 'Ultimate' ? 'warning' : digimon.lvl === 'Mega' ? 'danger' : 'dark' "> {{ digimon.lvl }}</b-button>
        </b-card>
    </div>
  </b-row>
</div>
  
</template>

<script>
import { BCard, BRow, BContainer, BForm } from 'bootstrap-vue'
import axios from 'axios'

export default {
components: {
    BCard,
    BRow,
    BContainer,
    BForm,
},
data() {
    return {
        items: [],
        search: '',
        selected: null,
        options: [
            { value: null, text: 'Filtre pelo level'},
            { value: 'In Training', text: 'In Training'},
            { value: 'Rookie', text: 'Rookie'},
            { value: 'Champion', text: 'Champion'},
            { value: 'Ultimate', text: 'Ultimate'},
            { value: 'Fresh', text: 'Fresh'},
            { value: 'Mega', text: 'Mega'},
        ],
    }

},
computed : {
    itemsFiltered() {
        let values = []
        values = this.items.filter((item) => {
            return(
                item.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1 ||
                item.lvl.toLowerCase().indexOf(this.search.toLowerCase()) > -1
            )
        })
        values = values.filter((item) => {
            if(this.selected === null ) {return item}
    
            return item.lvl === this.selected
        })
        return values
    },
},

created() {
    this.getDigimon()
},

methods: {

    async getDigimon() {
        axios.get('https://digimon-api.vercel.app/api/digimon').then(res => {
            res.data.map( digimon => {(
                this.items.push({
                    name: digimon.name,
                    img: digimon.img,
                    lvl: digimon.level,
                })
            )})
        })
    },
    
},


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

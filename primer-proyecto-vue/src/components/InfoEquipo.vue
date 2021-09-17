<template>
  <div>
        <h1>Mostrando info del equipo {{teamName}}</h1>
        <div v-if="result">
            <p>Nombre del quipo: {{this.equipo}}</p>
            <p>Nombre corto: {{this.nombreCorto}}</p>
            <p>Año formacion: {{this.añoFormacion}}</p>
            <p>Deporte: {{this.deporte}}</p>
            <p>Liga: {{this.liga}}</p>

        </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    data(){
        return{
            result: true,
            equipo: '',
            nombreCorto: '',
            añoFormacion: '',
            deporte: '',
            liga: ''
        }
    },
    props: ['teamName'],
    methods: {
        async getTeamDetails(){
            return axios.get(`https://www.thesportsdb.com/api/v1/json/1/searchteams.php?t=${this.teamName}`)
                .then((response) => {
                    console.log(response.data.teams)
                    let team = response.data.teams[0]

                    this.equipo = team.strTeam;
                    this.nombreCorto = team.strTeamShort;
                    this.añoFormacion = team.intFormedYear;
                    this.deporte = team.strSport;
                    this.liga = team.sterLeague;
                })
        }
    },
    watch: {
        teamName: async function(){
            await this.getTeamDetails();
        }
    }
}
</script>

<style>

</style>
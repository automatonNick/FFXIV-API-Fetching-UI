<template>
  <h1>{{loader}}</h1>
  <h1>{{ charData.Character.Name }}</h1>
  <p>
    {{ charData.Character.DC}} DC, {{charData.Character.Server}} Server

  </p>
  <div class="columns">


  <div class="col-1">

    <div class="col-1">
      <h2>Jobs</h2>

      <span v-for="(t, index) in charData.Character.ClassJobs" :key="index">
      <ul v-if="index<19">
        <img alt="Job Icon" v-if="index<19" class="classIcon" v-bind:src="'images/'+t.UnlockedState.Name+'.png'">
        <li v-if="index<19">
          {{ t.UnlockedState.Name }}
        </li>
        <li v-if="index<19">{{t.Level}}</li>
        <li v-if="index<19 && parseInt(t.Level)!=90 && parseInt(t.Level)!=0">{{parseInt(t.ExpLevel/t.ExpLevelMax*100)}}% XP</li>
      </ul>

      </span>
    </div>

  </div>
  <div class="col-3">

    <img class="charPicture" v-bind:src="charData.Character.Portrait" alt="Character Portrait">
    <h3>{{charData.Character.Nameday}}</h3>
    <div>
      <h2>{{charData.Character.ClassJobsBozjan.Name}}: {{charData.Character.ClassJobsBozjan.Level}}</h2>
    </div><div>
      <h2>{{charData.Character.ClassJobsElemental.Name}}: {{charData.Character.ClassJobsElemental.Level}}</h2>
    </div>
  </div>
<div class="column">
    <h2>Crafting</h2>
  <div style="display: flex">

      <div class="col-2" >
  <span v-for="(t, index) in charData.Character.ClassJobs" :key="index">
    <ul v-if="index>19">
      <li v-if="index>19">
        {{ t.UnlockedState.Name }}
      </li>
      <li v-if="index>19">{{t.Level}}</li>
      <li v-if="index>19 && parseInt(t.Level)!=90 && parseInt(t.Level)!=0" >{{parseInt(t.ExpLevel/t.ExpLevelMax*100)}}% XP</li>
      <img v-if="index>19 " class="classIcon" v-bind:src="'images/'+t.UnlockedState.Name+'.png'">
    </ul>
  </span>
      </div>
      </div>


</div>
  </div>
</template>

<script>
const API_URL = `https://xivapi.com/character/19120603`

  export default {
    data: () => ({
      charData: null,
      loader: "Loading character data"
    }),

    created() {
      // fetch on init
      this.fetchData()
    },


    methods: {
      async fetchData() {
        await fetch(API_URL)
            .then((response) => response.json())
            .then((data) => {
              this.loader="";
              this.charData = data;
            });
      },
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.charPicture{
  height: 600px;
}
.columns{
  display: flex;

  justify-content: space-evenly;
}
.classIcon{

  height: 25px;
  width: 25px;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  text-align: right;
  display: flex;
  justify-content: space-between;
}
li {

  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

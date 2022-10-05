<style lang="scss" scoped>
  .box.box-activy{
    position: relative;
    display: block;
    width: 250px;
    border: 2px;
  }

  .page-wraper{
  background-color : #EAEFF3;
}
</style>
<template>
 <div class="page-wraper">
  <div class="container">
    <div class="is-flex is-justify-content-space-between pb-3">
      <div class="is-inline-flex is-align-items-start is-flex-direction-column">
        <div class="title has-text-black is-size-2 py-6">Activity</div>
      </div>
      <div class="is-flex is-align-items-justify py-6">
       <div class="buttons">
          <b-button rounded class="button is-medium is-info" icon-left="plus" @click="created">Tambah</b-button>
        </div>
      </div>
    </div>
    <div class="is-relative is-block">
      <div class="columns is-mobile is-multiline is-variable mb-0">
        <div v-for="item in data" class="column is-12-mobile is-narrow-tablet" :key="item.id">
          <n-link :to="`${path}/${item.id}`">
          <div class="box box-activy">
            <div class="subtitle has-text-black is-size-5">{{item.title}}</div>
             <div class="is-flex is-justify-content-space-between">
              <div class="is-inline-flex is-align-items-start is-flex-direction-column">
                <p class="has-text-grey is-size-6 py-6 mt-6">5 Oktober 2022</p>
                </div>
                <div class="is-flex is-align-items-justify py-6">
                  <img class="icon mt-6" src="~assets/delete.png">
                </div>
              </div>
          </div>
          </n-link>
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'IndexPage',
  layout: 'default',

   data() {
    return {
      data: [],
      path: '/activity',
      activityId: null
      }
    },

     mounted() {
  this.fetchData();
  this.created();
},

methods:{
async fetchData(){
  try {
    let {data} =  await axios.get('https://todo.api.devcode.gethired.id/todo-items?activity_group_id=5').then(response => {this.data = response.data.data; });
    console.log(data);
    this.data  = data
  } catch (err) {
    console.log(err)
  }
 },

async created(){
  try{
    let activity = { activity_group_id: "5" , title: "New Activity", _comment: "list of priority is : very-high, high, normal, low, very-low | defalut value is very-high"}
    let response = await axios.post("https://todo.api.devcode.gethired.id/todo-items", activity);
      this.activityId = response.data.id;
  } catch (err) {
    console.log(err)
  }
}
}
}
</script>

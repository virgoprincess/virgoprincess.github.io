<template>
  <div class="overview-settings">
    <b-container fluid class="overview-form" >
        <b-row>
          <b-col cols="3">
            <h5>Overview</h5>
          </b-col>
          <b-col class="align-right">
            <b-btn class="btn-save">Save</b-btn>
          </b-col>
        </b-row>
        <b-row>
          <b-col cols="3">
            <label for="">Company Name</label>
          </b-col>
          <b-col class="d-flex gap-3">
            <b-form-input type="text" placeholder="Company Name"></b-form-input>
          </b-col>
        </b-row>

        <b-row>
          <b-col cols="3">
            <label>Date Created</label>
            <p class="desc">Send verification code to:</p>
          </b-col>
          <b-col class="align-right">
            <p>Jan 15, 2018</p>
          </b-col>
        </b-row>

        <b-row>
          <b-col cols="3">
            <label>Term of Service</label>
          </b-col>
          <b-col class="gap-3 align-right">
            <b-link href="www.sphyr.com/termofservice">www.sphyr.com/termofservice</b-link>
          </b-col>
        </b-row>

        <div class="d-flex justify-content-between">
        <h5>Members</h5>
        <div class="d-flex align-items-center gap-2">
          <b-input-group class="search-member">
            <b-icon-search />
            <b-form-input  v-model="search"  placeholder="Search" autocomplete="off" ></b-form-input>
          </b-input-group>
          <b-button class="btn-add">
              <b-icon-plus />
          </b-button>
        </div>
      </div>

      <div class="members-list scrollable">
        <b-table small :items="filteredData" :fields="fields" responsive="sm">
        </b-table>
        <!-- <table class="tabletable-bordered">
          <thead>
            <tr>
              <th>Name</th>
              <th>Email Address</th>
              <th>Role</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(member, i) in members" :key="i">
              <td>
                <b-img
                  class="logo"
                  rounded="circle"
                  :src="require('@/assets/images/image-file-3.jpg')"
                  alt="Left image"
                ></b-img>
                {{member.name}} 
              </td>
              <td class="fw-700">{{ member.email}}</td>
              <td> {{member.role}} </td>
            </tr>
          </tbody>
        </table> -->
      </div>

      </b-container>
  </div>
</template>
<script>
export default {
  name:'OverviewSettings',
  mounted(){
    this.setupTable();
  },
   methods:{
    setupTable(){
      this.filteredData = this.members;
    }
  },
  data(){
    return{
      fields:[
        {
          key:'name',
          sortable:true,
        },
        {
          key:'emailAddress',
          sortable:true,
        },
        {
          key:'role',
          sortable:true,
        },
      ],
      members:[
        { name:'James Stewart', emailAddress:'stewartJ@gmail.com', role:'Admin'},
        { name:'Jane Williams', emailAddress:'janeW@gmail.com', role:'Owner'},
        { name:'Tony Roberts', emailAddress:'rob123@gmail.com', role:'User'},
        { name:'Joseph Adams', emailAddress:'josam11@gmail.com', role:'User'},
        { name:'Ray Smith', emailAddress:'raysun@gmail.com', role:'Guest'},
        { name:'James Bond', emailAddress:'bondpaper@gmail.com', role:'Admin'},
        { name:'Rachel Williams', emailAddress:'willra@gmail.com', role:'Owner'},
        { name:'Julia Roberts', emailAddress:'robj@gmail.com', role:'User'},
        { name:'Joseph Marco', emailAddress:'jmsilence@gmail.com', role:'User'},
        { name:'Ray Velasco', emailAddress:'velascor@gmail.com', role:'Guest'},
      ],
      search:'',
      filteredData:[],
    }
  },
  watch:{
    search(){
      this.filteredData = this.members.filter(member => {
        return member.name.toLowerCase().match(this.search.toString().toLowerCase()) || member.emailAddress.toLowerCase().match(this.search.toString().toLowerCase()) || member.role.toLowerCase().match(this.search.toString().toLowerCase());
      });
    }
  }
}
</script>
<style lang="scss" scoped>
.overview-settings::v-deep{
  /* padding: 30px 50px; */
  max-height: 77vh;
  .search-member{
    border: 1px solid $light-gray;
    padding-left: 5px;
    background-color: white;
    align-items: center;
    border-radius: 0.25rem;
    width: 350px;
    svg{ color: $light-gray; }
    input{
      color: $black;
      background-color: transparent;
      padding: 0 0 0 5px;
      border: 0;
    }
    input::placeholder{
      font-style: normal;
    }
  }
  .btn-add,.btn-add:focus,.btn-add:hover{ width: 50px;background-color: #fff; border-color:$light-gray; height:45px;color: $black;}
  .members-list{ max-height: 55vh;}
/* .tabletable-bordered{ width: 100%; }
  
  table {
  border-collapse: separate;
  border-spacing: 0 15px;
  }
  th,
  td {
    text-align: left;
    border-bottom: 1px solid $light-gray;
    padding: 10px;
    img {
      width: 50px;
      height: 50px;
    }
  }
  th {
    position: sticky;
    position: -webkit-sticky;
    background-color: $background-color;
    top: 0;
  } */
   th{
    background-image: none !important;
    width: 33.33%;
  }
  img {
      width: 50px;
      height: 50px;
    }
  .sr-only{
    display: none;
  }
}
</style>
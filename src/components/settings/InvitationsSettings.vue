<template>
  <div class="invitations-settings">
    <b-container fluid class="invitation-form" >
        <b-row>
          <b-col cols="3">
            <h5>Invitations</h5>
          </b-col>
          <b-col class="align-right">
            <b-btn class="btn-fit btn-outline">Send Invite</b-btn>
          </b-col>
        </b-row>
        
      <div class="members-list scrollable">
        <b-table small responsive="sm" :items="members" :fields="fields" >
          <template #cell(status)="data">
            <div class="member-status" :class="data.item.status.toLowerCase() === 'accepted' ? 'green-highlight' :'red-highlight'">
              <b-icon-check2 v-show="data.item.status.toLowerCase() == 'accepted'"/> {{data.item.status}}
            </div> 
          </template>
        </b-table>
        <!-- <table class="tabletable-bordered">
          <thead>
            <tr>
              <th>Name</th>
              <th>Email Address</th>
              <th>Invited By</th>
              <th>Date</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(member, i) in members" :key="i">
              <td> {{member.name}} </td>
              <td>{{ member.email }}</td>
              <td>{{ member.invitedBy}}</td>
              <td>{{member.date}} </td>
              <td> 
                <div class="member-status" :class="member.status.toLowerCase() === 'accepted' ? 'accepted' :'pending'">
                  <b-icon-check2/> {{member.status}}
                </div> 
              </td>
            </tr>
          </tbody>
        </table> -->
      </div>

      </b-container>
  </div>
</template>
<script>
export default {
  name:'InvitationsSettings',
  data(){
    return{
      fields:[
        {
          key:'name',
          sortable:true,
        },
        {
          key:'email',
          label:'Email Address',
          sortable:true,
        },
        {
          key:'invitedBy',
          sortable:true,
        },
        {
          key:'date',
          sortable:true,
        },
        {
          key:'status',
          sortable:true,
        }
      ],
      members:[
        { name:'James Stewart', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Accepted'},
        { name:'Rachel Williams', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Pending'},
        { name:'Tony Roberts', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Accepted'},
        { name:'Joseph Adams', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Accepted'},
        { name:'Ray Smith', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Pending'},
        { name:'James Stewart', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Accepted'},
        { name:'Rachel Williams', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Accepted'},
        { name:'Tony Roberts', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Accepted'},
        { name:'Joseph Adams', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Accepted'},
        { name:'Ray Smith', email:'email@gmail.com', invitedBy:'Jessica Shaw', date:'Dec. 1, 2022', status:'Accepted'},
      ]
    }
  }
}
</script>
<style lang="scss" scoped>
.invitations-settings::v-deep{
  max-height: 71vh;
  .row:first-child{
    border-bottom: 0;
    margin-bottom: 0px;
  }
  th{
    background-image: none !important;
    /* width: 33.33%; */
  }
  img {
      width: 50px;
      height: 50px;
    }
  .sr-only{
    display: none;
  }
}
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
  }
  .pending{
    color: $brown;
    background-color:$light-brown;
  }
  .accepted{ 
    color: $medium-green;
    background-color:$light-green;
   }
  .member-status{
    font-weight: 600;
    width: fit-content;
    text-align: center;
    padding: 5px 10px;
    border-radius: 90px;
  } */
  .members-list{
    max-height: 77vh;
  }
</style>
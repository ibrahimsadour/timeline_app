<template>
    <Page>
        <ActionBar title="timeline"/>
          <GridLayout verticalAlignment="top" columns="50,150,*" rows="70,auto,auto"  orientation="horizontal" class="post" >
              
                <ListView class="list-group" for="item in lists" @itemTap="onItemTap" style="height:1250px">
                    <v-template>
                    <FlexboxLayout flexDirection="row" class="list-group-item">
                        <Label :text="item.id" class="list-group-item-heading" style="width: 100%" />
                        
                        <Label :text="item.title" class="list-group-item-heading" style="width: 100%" />
                    </FlexboxLayout>
                    </v-template>
                </ListView>
        </GridLayout>
  
    </Page>
    
</template>

<script lang="ts">
    import Vue from 'vue'
    import axios from 'axios'
    import VueAxios from 'vue-axios'
    Vue.use(VueAxios, axios)

    export default {
        
        data() {
            return {
                msg: 'User Nameff ',
                time_post: 'Friday 10:00',
                lists: []
                
            };
        },
        
        methods: {
            onItemTap($event) {
            }
        },
        mounted() {

            let url = 'https://a6323df33c31.ngrok.io/api/get-post'

            axios({
                url: url,
                method: "GET",
                headers: { "Content-Type": "application/json" ,"Accept": "application/json"},
                
            }).then((response) => {
                
                const result = response.data;
                console.log(result);
                this.lists = result;
            }, (e) => {
                console.log(e);
            });
            

        }
    };
</script>


  <style scoped>
      .ActionBar {
          color: #FFFFFF;
      }
      .name {
          vertical-align: center;
          font-size: 17;
          color: #000000;
          font-weight: 700;
          height: 50;
          margin-left: 15;
      }
      
      .avatar {
          width: 50;
          height: 50;
          border-radius:50%;
      }
      .post{
       width: auto;
       height: auto;
       border-radius: 15px;
       padding: 20 20 10 20;
       margin: 13;
       android-elevation:6;
      }
      .time_post {
        vertical-align: center;
        font-weight: 700;
        color: #C0C0C0;
        height: 50;
        margin-left: 15;
        margin-top: 50;
      }
      .post_message{
        width: auto;
        font-size: 12;
        line-height: 1.7;
        
      }
      .Image_post {
        width: auto;
        text-align: left;
        border-radius: 5;
        height: 250;
        margin-top: 10;
        margin-bottom: 20;
      }
</style>



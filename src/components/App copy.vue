<template>
    <Page>
        <ActionBar title="timeline"/>
          <GridLayout verticalAlignment="top" columns="50,150,*" rows="70,auto,auto"  orientation="horizontal" class="post" >
              <!-- Image with stretch property ("none", "aspectFill" and "aspectFit") -->
              <Image row="0" col="0" rowSpan="1" src="https://www.pngitem.com/pimgs/m/78-786501_black-avatar-png-user-icon-png-transparent-png.png"  stretch="aspectFill" class="avatar"></Image>
              <Label row="0" col="1" rowSpan="1" class="name" :text="msg"/>
              <Label row="0" col="1" rowSpan="1" class="time_post" :text="time_post"/>
              <Label row="1" col="0" colSpan="3"  textWrap="true" class="post_message">
                <FormattedString >
                  <Span text="This text has a " />
                  <Span text="red " style="color: red" />
                  <Span text="piece of text. " />
                  <Span text="Also, this bit is italic, " fontStyle="italic" />
                  <Span text="and this bit is bold." fontWeight="bold" />
                  <Span text="Start het videogesprek doormiddel van de accepteer knop hieronder in te drukken. De behandelaar start het gesprek vanzelf." fontWeight="bold" />
                </FormattedString>
              </Label>
              <Image row="2" col="0" colSpan="3" src="https://imgcomfort.com/Userfiles/Upload/images/illustration-geiranger.jpg"  stretch="aspectFill" class="Image_post"></Image>
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
                lists: ""
                
            };
        },
        
        methods: {
            onItemTap($event) {
            }
        },
        mounted() {

            let url = 'http://localhost:8000/api/get-post'
            axios({
                url: url,
                method: "GET",
                headers: { "Content-Type": "application/json" },
            }).then((response) => {
                const result = response.data;
                this.lists = result;
                console.log(result);
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



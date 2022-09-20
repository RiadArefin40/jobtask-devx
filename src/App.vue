

<template>
   <div class="navbar d-flex text-white bg-dark ">
      <h3 class="p-4 mx-3">Dashboard</h3>
      <div class="d-flex ">
         <i class="fa-solid fa-user-tie fs-1"></i>
         <h3 class=" mx-2">Demo User</h3>
     
      </div>
    
     
   </div>
   <User :items="collapsibleItems"/>
   
</template>

<script>
 
  import User from './components/Dashboard.vue'
  import {ref}from'vue'
   export default{
    name:"App",

     setup(){
       const collapsibleItems= ref([   { id:1,
           header:'User',
           body:'<div class="text-white"><h1 class="text-center">User</h1><p>Where can I get some?There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form, by injected humour, or randomised words which dont look even slightly believable. If you are going to use a passage of Lorem Ipsum, you need to be sure there isnt anything embarrassing hidden in the middle of text. All the Lorem Ipsum generators on the Internet tend to repeat predefined chunks as necessary, making this the first true generator on the Internet. It uses a dictionary of over 200 Latin words, combined with a handful of model sentence structures, to generate Lorem Ipsum which looks reasonable. The generated Lorem Ipsum is therefore always free from repetition, injected humour, or non-characteristic words etc.</p></div>',
          upper:true,
            icon:true,
           active:false,
           toggle:true,
         },
           {id:2,
           header:'View-Content',
            body:'<div class="text-white"> <div class="  p-2"> <u><h3 class="text-info">View Content</h3></u> </div> <h1 class="text-center">View</h1> <b>What is lorem ipsam?</b>  <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p> <b>Why do we use it?</b> <p>It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for lorem ipsum will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose injected humour and the like.</div></p>',
            upper:false,
           icon:false,
           active:true,
            toggle:true,
         },]);

      return{
         collapsibleItems:collapsibleItems
      }
     },
     components:{
      User,
      
     }
    //--------------------Options Api-------------------
   //   data(){
   //   return{
   //     collapsibleItems:[
   //        { id:1,
   //         header:'User',
   //         body:'<div class="text-white">Where can I get some?There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form, by injected humour, or randomised words which dont look even slightly believable. If you are going to use a passage of Lorem Ipsum, you need to be sure there isnt anything embarrassing hidden in the middle of text. All the Lorem Ipsum generators on the Internet tend to repeat predefined chunks as necessary, making this the first true generator on the Internet. It uses a dictionary of over 200 Latin words, combined with a handful of model sentence structures, to generate Lorem Ipsum which looks reasonable. The generated Lorem Ipsum is therefore always free from repetition, injected humour, or non-characteristic words etc.</div>',
   //        upper:true,
   //          icon:true,
   //         active:false,
   //         toggle:true,
   //     },
   //         {id:2,
   //         header:'View-Content',
   //          body:'<div class="text-white"> <div class="  p-2"> <u><h3 class="text-info">View Content</h3></u> </div> <h1 class="text-center">View</h1> <b>What is lorem ipsam?</b>  <p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industrys standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p> <b>Why do we use it?</b> <p>It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for lorem ipsum will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose injected humour and the like.</div></p>',
   //          upper:false,
   //          icon:false,
   //          active:true,
   //          toggle:true,
   //        },
   //     ]
   //   }
   //   },
   //  components:{
   //   User,
   //  }

   }

</script>
<style scoped>
          /* code for animation with Vue Transition  */
 
 
          .collapse-enter-active{
            height: 30px;  
           }
           .collapse-enter-to{
             height: 500px;
           }
           .collapse-leave-to{
             height: 30px;   
           }
             .cursor{
             cursor: pointer;
           }
           .toggle-enter-from{
           transition: all 3s linear;
           }
           .toggle-enter-to{
            transition: all 3s linear;
           }
         .toggle-leave-active{
              transition: all 2s cubic-bezier(1, 0.8, 0.8, 1);
         
         }
           .toggle-leave-to{
              transform: translatey(100px);
             opacity: 0;
           }
</style>


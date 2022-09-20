<template>
<div class="dashboard d-flex flex-row-reverse justify-content-between ">
    <div class="collapse-wrapper ">
    
    <div  v-for="(item,index) in customItems" :key="item.header"  class="collapsible-item mx-5">
        <Transition name=toggle>
            
               <div v-if="!item.toggle"  @click="reverse(index)"    class="collapsible-header d-flex text-center rounded-pill mt-3">
               <h4 class="mx-auto"> {{item.header}}</h4>
              
               <!-- <i v-if="item.active" @click.stop="activateBody(index)" class="fa-solid fa-xmark cursor fs-2 "></i> -->
              
                <i v-if="!item.active  " @click.stop="activateBody(index)" class="fa-solid fa-sort-down cursor fs-2 mx-3"></i> 
               
          
            </div>
         </Transition>
        <Transition name="collapse">
            <div v-html="item.body" v-if="item.active" class="  collapsible-body">
           
           </div>
        </Transition>
    </div> 
    </div> 
    <div>
         <div class="menu-bar p-4">
            <img class="" src="https://i.ibb.co/LkR6fq2/001-demo.png" alt="">
        </div>
         <div class=" left-menu d-flex p-5">
       
        <div class="befor-hover  ">
        
           <i @mouseover="hover()" @mouseleave="leave()" class="fa-solid fa-house text-white fs-1 p-2 bg-danger rounded-circle"></i>
        </div>
        <div  class="after-hover">
          <h1 v-if=" customItems[0].home" class="text-white p-2 ">Home</h1>
        </div>
           
        
                
     </div>
    </div>
    
  </div>   
</template>
<script>
//import{computed,ref,toRefs} from 'vue'
export default {
    name:'Dashboard',
    props:[
      "items"
    ],

    //  setup(props){
    //    const collapsibleItems= ref([]);
    //    const { items } = toRefs(props)
    //     const customItems=computed(function(){
    //        collapsibleItems=items.map((item)=>{
    //          return{
    //              header:item.header,
    //                body:item.body,
    //                active:item.active,
    //               icon:item.icon
    //           }
    //         });
    //         return collapsibleItems
    //   });
 

    //  return{
    //   customItems
    //  }
    //  },
   
    data(){

        return{
              collapsibleItems:[],
              menu:[

              ]
         }
     },
      computed:{
         customItems(){
             this.collapsibleItems=this.items.map((item)=>{
                   return{
                 header:item.header,
                 body:item.body,
                 active:item.active,
                 icon:item.icon,
                 home:item.home,
             }
             }
             );
             return this.collapsibleItems;
         }
      },


    methods:{
        activateBody(index,event){
            console.log(index);
            this.collapsibleItems[1].active = !this.collapsibleItems[1].active;
            this.collapsibleItems.forEach((item,id)=>{
                if(id!==index){
                 item.active=false;
                }
            })
        
        },
     
        reverse(index){
           
            if(index==0 && !this.collapsibleItems[1].active){
               
                this.collapsibleItems[0].toggle= !this.collapsibleItems[0].toggle;
               
             setTimeout(()=>{ 
                 this.collapsibleItems[1].toggle= false;
                 this.collapsibleItems[0].toggle= false;
                 this.collapsibleItems= this.collapsibleItems.reverse();
                 console.log('sett')
                }, 1000);

            }
           
           
        },

        hover(){
            console.log('hover');
            this.collapsibleItems[0].home=! this.collapsibleItems[0].home;
      
           
        },
        leave(){
          console.log('leave');
          this.collapsibleItems[0].home=! this.collapsibleItems[0].home;
        }

    }
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
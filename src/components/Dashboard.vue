<template>
<div class="dashboard d-flex flex-row-reverse justify-content-between ">
    <div class="collapse-wrapper ">
    
    <div  v-for="(item,index) in customItems" :key="item.header"  class="collapsible-item mx-5">
        <Transition name="toggle">
             <div v-if="!item.toggle"  @click="reverse(index)"    class="collapsible-header d-flex justify-content-between  ">
               <h4> {{item.header}}</h4>
               <i v-if="item.active" @click.stop="activateBody(index)" class="fa-solid fa-xmark cursor fs-2 "></i>
               <i v-if="!item.active" @click.stop="activateBody(index)" class="fa-solid fa-sort-down cursor fs-2 "></i>
           </div>
         </Transition>
        <Transition name="collapse">
            <div v-html="item.body" v-if="item.active" class="  collapsible-body">
           
           </div>
        </Transition>
    </div> 
    </div> 
      <div class="menu-bar d-flex p-5">
           <i class="fa-solid fa-house text-white fs-1"></i>
          <h1   @mouseover="hover()" @mouseleave="leave()"
                 class="text-white ">Home</h1>
                
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
              collapsibleItems:[]
         }
     },
      computed:{
         customItems(){
             this.collapsibleItems=this.items.map((item)=>{
                   return{
                 header:item.header,
                 body:item.body,
                  active:item.active,
                  icon:item.icon
             }
             }
             );
             return this.collapsibleItems;
         }
      },


    methods:{
        activateBody(index,event){
            console.log(index);
            this.collapsibleItems[index].active = !this.collapsibleItems[index].active;
            this.collapsibleItems.forEach((item,id)=>{
                if(id!==index){
                 item.active=false;
                }
            })
        
        },
     
        reverse(index){
            console.log('reverse');
           
            this.collapsibleItems[index].toggle= !this.collapsibleItems[index].toggle;
          
           setTimeout(()=>{ 
               this.collapsibleItems[1].toggle= false;
                this.collapsibleItems[0].toggle= false;
                 this.collapsibleItems= this.collapsibleItems.reverse();
               console.log('sett')
          }, 1000);
        },

        hover(){
          console.log('hover');
            this.collapsibleItems[1].active = !this.collapsibleItems[1].active;
           
        },
        leave(){
          console.log('leave');
            this.collapsibleItems[1].active = !this.collapsibleItems[1].active;
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
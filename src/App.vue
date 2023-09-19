<script>
 export default {
  
  data(){
    return{
      enteredValue:'',
      goals:[
        {id:1, name:'Shopping'}
      ],
      cancel:true,
      handleGoalById:null,
      
      
    }
    
  },
  methods:{
    addNew(){
      if(this.handleGoalById!=null){
        let editGoal=this.goals.find((goal)=>goal.id==this.handleGoalById)
        editGoal.name=this.enteredValue
        this.handleGoalById=null
        this.enteredValue=''
      }
      else if(this.enteredValue==''){
        this.error=true
        this.errorHandler='Input is empty'
      } else {
       let newGoal= {
        id:this.goals.length+1,
        name:this.enteredValue
       }
       this.goals.push(newGoal)
       
       this.enteredValue=''
   
   
      }
   
    },
      
    editToDo(id){
      let editGoal=this.goals.find((goal)=>goal.id==id)
      this.enteredValue=editGoal.name
      this.handleGoalById=id

    },
    cancelClick(id){
     this.goals=this.goals.filter((goal)=>goal.id!=id)
    }

  }
 }
</script>

<template>
 
   <div class="container">
    <div class="header">
      <h1>TODO LIST</h1>
       <input type="text" name="" id="" placeholder="Write your todo list here..." v-model="enteredValue">
       <button class="addNew" @click="addNew">ADD</button>
    </div>
    <div class="main">
      <h2>LIST OF WORKS TODO</h2>
      <ul  >
        <div ref="styles">
          <li v-for="goal in goals">
            
            {{ goal.id }}
        {{ goal.name }}

        <div class="iconsAdd">
           
           <button class="editToDo" @click="editToDo(goal.id)">EDIT</button>
           <i @click="cancelClick(goal.id)" class="fa-solid fa-x"></i>
     </div>
    </li>
        </div>
          
           
          
    
       

        
        
      </ul>
      
    </div>
       
   </div>
</template>

<style scoped>
@import url(https://fonts.googleapis.com/css2?family=Rubik:wght@100;200;300;400;500;600;800;900&display=swap);
@import url(https://fonts.googleapis.com/css2?family=Dancing+Script:wght@100;200;300;400;500;600;700&display=swap);

body {
  
}
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
     
 body {
       font-family: 'Rubik', sans-serif;
 }
    
   
  .container{
    display: flex;
    /* justify-content: center; */
    flex-direction: column;
    box-shadow: 2px 2px 2px #222;
    border: 1px solid #222;
    width: 600px;
    height: 400px;
    margin-left: 450px;
    margin-top: 50px;
    border-radius: 10px;
    
  }
  .header{
    background-color: rgb(32, 144, 214);
    width: 100%;
    height: 100px;
    border-radius: 10px 10px 0 0;
    text-align: center;
    font-family: 'Rubik', sans-serif;
    
    /* display: flex; */

  }
  h1{
    width: 100%;
    margin: 7px 0;
    font-family: 'Rubik', sans-serif;
  }
  input{
    width: 450px;
    height: 30px;
    border-radius: 5px;
    padding: 7px;
    
  }
  .addNew{
    margin-left: 8px;
    height: 30px;
    width: 80px;
    border-radius: 5px;
    font-family: 'Rubik', sans-serif;
    cursor: pointer;
  }
  .main{
    
  }
  h2{
    text-align: center;
    margin: 10px;
    font-family: 'Rubik', sans-serif;
  }
  ul{
    list-style: none;
    display: block;
     width: 100%;
     box-sizing: border-box;
    

  }
  li{
    background-color: rgb(231, 224, 224);
    width: 95%;
    height: 35px;
    margin-left: 10px;
    margin-top: 5px;
    border-radius: 5px;
    padding: 7px 20px;
    font-size: 18px;
    display: flex;
    justify-content: space-between;
    font-family: 'Dancing Script', handwriting;
    font-weight: bold;
  }
  .checked{
   filter: blur(.5px);
    
  }
  .iconsAdd{
    display: flex;
     gap: 10px;
     font-family: 'Rubik', sans-serif;
  }
  /* .checkToDo{
    border: none;
    background: none;
  } */
.editToDo{
  border: none;
  background: none;
  font-family: 'Rubik', sans-serif;
  cursor: pointer;
}
.picked{
  
  font-size: 13px;
   margin-top: 3px;
   color: green;
   cursor: pointer;
}
.fa-check{
  width: 25px;
  height: 25px;
  color: rgb(32, 144, 214);
  text-align: center;
  cursor: pointer;
}
.fa-x{
  position: relative;
  width: 25px;
  box-sizing: border-box;
  color: red;
  text-align: center;
  cursor: pointer;

}
.fa-x:hover{
  transform: scale(1.2);
  transition: all .5s;
  
}
.fa-check:hover{
  transform: scale(1.2);
  transition: all .5s;
}
.editToDo:hover{
  transform: scale(1.1);
  transition: all .5s;
  
}




</style>

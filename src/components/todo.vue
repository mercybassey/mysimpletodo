<template>

    <div>
        
            <div><br><br>
            
                <button class="btn btn-info" style="border: none; margin-top: 30px; margin-left: 150px; " @click="deleteAll">Delete All To-do</button>

                <div class=" container bod pb-4" ><br><br>

                    

                        <div class="container">
                            <div class="row">
                                <div class="col-lg-6" >
                                        <table class="table border shadow" >
                                                <thead>
                                                <tr>
                                                    <th scope="col">id</th>
                                                    <th scope="col">todo</th>
                                                    <th scope="col">priority</th>
                                                    <th scope="col">description</th>
                                                    <th scope="col">Deadline</th>
                                                    <th scope="col">Time</th>
                                                    <th scope="col">Date</th>
                                                    <th scope="col">Edit</th>
                                                    <th scope="col">Delete</th>
                                                    <th scope="col">Done</th>
                                                
                                                </tr>
                                                </thead>
                                                <tbody>
                                                <tr v-for="(person,index) in persons">
                                                        <th scope="row">{{parseInt(index) +1}}</th>
                                                        <td>{{person.todo}}</td>
                                                        <td>{{person.priority}}</td>
                                                        <td>{{person.description}}</td>
                                                        <td>{{person.deadline}}</td>
                                                        <td>{{person.time}}</td>
                                                        <td>{{person.date}}</td>
                                                        
                                                        <td>
                                                            
                                                        <button @click="updateTodo(index)" style="border: none; background-color: rgb(70, 75, 73)55, 141);"><i class="fa fa-cog"></i></button>

                                                        </td>
                                                        <td>
                                                        <button @click="deleteTodo(index)" style="border: none; background-color: rgb(70,75,73)55, 141);"><i class="fa fa-trash"></i></button>

                                                        </td>
                                                        <td>{{person.done}}</td>
                                                </tr>
                                                
                                                    
                                                </tbody>
                                        </table>
                                </div>
                                        
                                        
                                <div class="col-lg-3" style="margin-left: 800px; margin-top: -200px;">
                                    <div class="card shadow p-4">
                                        <h2 class="mb-4">Please Add Your To-do</h2>
                                        <p></p>

                                        <form @submit.prevent="addUser">
                                                <div class="form-group">
                                                    <label>To-do</label>
                                                    <input v-model="user.todo" type="text" id="name" class="form-control">
                                                </div>
                                                <div class="form-group">
                                                    <label>Priority</label>
                                                    <select v-model="user.priority">
                                                        <option value="Important">Important</option>
                                                        <option value="Urgent and Important">Urgent and Important</option>
                                                        <option value="Urgent">Urgent</option>
                                                    </select>
                                                </div>
                                                <div class="form-group">
                                                    <label>Description</label>
                                                    <input v-model="user.description" type="text" id="role" class="form-control">
                                            </div>
                                            <div class="form-group">
                                                    <label>Deadline</label>
                                                    <input v-model="user.deadline " type="text" id="role" class="form-control">
                                                </div>
                                                <div class="form-group">
                                                    <label>Time</label>
                                                    <input v-model="user.time" type="text" id="role" class="form-control">
                                                </div>
                                                <div class="form-group">
                                                    <label>Date</label>
                                                    <input v-model="user.date" type="text" id="role" class="form-control">
                                                </div>
                                                <div class="form-group">
                                                    <label>done</label>
                                                    <select v-model="user.done">
                                                        <option value="Yes">Yes</option>
                                                        <option value="No">No</option>
                                                        <option value="Pending">Pending</option>
                                                    </select>
                                                </div>
                                                <div class="form-group">
                                                        
                                                        <button v-if="status" type="submit" class="btn btn-primary" @click="addTodo">Add to do</button>
                                                        <button v-else type="submit" @click.prevent="updatePerson" class="btn btn-primary" >Update</button>
                                                        <button type="submit" id="reset" class="btn btn-danger" @click="changeStatus" ml-4>reset</button>
                                                        
                                                </div>
                                        </form>
                                    </div>
                                
                                </div>
                    </div>  </div>
            </div>
        </div>
        
    </div>

</template>



<script>
export default {
    data(){
        return{
               user: {
            todo: "",
            priority: "",
            description: " ",
            deadline: "",
            time: " ",
            date: " ",
            done: " "
             
        },
        status: true,
        index: null,
        
        persons: [
            {todo:"Smell the roses", priority:"important",description:"Buy roses for my wedding",deadline:"wednessday", time:"3:00pm", date:"12/2/2020" , done:"Yes"},
            
        ]       
        }

    },
    methods:{
        
         changeStatus(){
            this.status = true
            this.user =  {
                todo: "",
                priority: "",
                description: " ",
                deadline: "",
                time: " ",
                date: " ",
                done: " "
            }
        },
        addTodo(){
            this.persons.push(this.user);
            this.user=" ";
            this.changeStatus();
        },
        editTodo(id){
            this.user = id;
            this.status = !this.status;
        },
        deleteTodo(index){
            this.persons.splice(index,1);
        },
        addSubmit(){
            this.status=!this.status;
        },
        updateTodo(id){
            this.user = this.persons[id];
            this.index = id
            this.status = !this.status;
        },
        updatePerson(){
            this.persons[this.index] = this.user;
            this.user = {
                todo: "",
                priority: "",
                description: " ",
                deadline: "",
                time: " ",
                date: " ",
                done: " "
            }
            this.status = !this.status
        },
        deleteAll(){
            this.persons = null;
        }
    }

}
</script>


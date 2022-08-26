<script>
	let validatename,validatepassword;
 import {
    Form,
    FormGroup,
    TextInput,
    PasswordInput,
Button,
  } from "carbon-components-svelte";
import { navigate } from "svelte-routing";



 function showdetails(){
  
  let getobj =window.localStorage.getItem("signupinfo")||"[]";
  let getobject = JSON.parse(getobj);

for(var i=0; i<getobj.length;i++){
 const name= getobject[i]?.name;
const getpassword = getobject[i]?.password;
  if((name == validatename) && (getpassword == validatepassword)){
    navigate("/details");
  }
  else{
console.log("Invalid message");
  }
  
}
 }
  
</script>
<h1>Welcome to Signin page!!!</h1>
<div class = "box">
<Form>
    <FormGroup>
    <TextInput  bind:value = {validatename} labelText="User name" placeholder="User name..." required />

<PasswordInput bind:value = {validatepassword}
  required
  type="password"
  labelText="Password"
  placeholder="password..."
/>
<Button expressive kind="danger"  on:click = {showdetails}>Next</Button>
   </FormGroup>
</Form>
</div>
<style>
    .box{
box-sizing: border-box;
padding: 20px;
border-radius: 20px;
background-color: rgb(205, 244, 244);
margin-top:10rem;
margin-left: 30rem;
width:40vw;
    }
    h1{
      font-size: 5rem;
      color:rgb(246, 119, 253);
      font-weight: 1000;
      display: flex;
      justify-content: center;
      position: relative;
      top:50px;
    }
</style>
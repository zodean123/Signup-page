<script>
  import { navigate } from "svelte-routing";
    import {
    FluidForm,
    FormGroup,
    TextInput,
    PasswordInput,
    Button,
     Modal
  } from "carbon-components-svelte";
  let open = false;
  let id,name,email,mobile,profession,password;
let valid=false;


  function getdetails(){
   let data ={
     "id":id,
    "name":name,
    "email":email,
    "mobile": mobile,
    "profession":profession,
    "password":password,
   }

   
  let signupdetails = window.localStorage.getItem("signupinfo")||"[]";
  let signupobj= JSON.parse(signupdetails);
  signupobj.push(data);
  window.localStorage.setItem("signupinfo",JSON.stringify(signupobj));


 if(document.getElementById('validate').value == '')
alert("Please fill the form");
else
navigate("/login");
 }

</script>

<h1 class = "signup">Sign up</h1>
<div class = "my">
<Button expressive kind="danger" on:click = { ()=> (open=true)} class = "my"><h3>Signup</h3></Button>
<Modal bind:open
modalHeading = "Sign up" 
primaryButtonText="Close"
on:click:button--primary={()=>open=false}
>
    <FluidForm on:submit >
     
    <FormGroup>
        <TextInput id="validate" required  bind:value={id}  labelText="ID" placeholder=" User ID..." />
        
        <TextInput  bind:value={name}  labelText="User name" placeholder=" User name..." required />
        
        <TextInput  bind:value={email}  labelText="Email" placeholder=" Email..." required />
        
        <TextInput  bind:value={mobile}  labelText="Mobile" placeholder=" Mobile..." required />
        
        <TextInput  bind:value={profession}  labelText="Profession" placeholder=" Profession..." required />
        <PasswordInput  bind:value={password}
          required
          type="password"
      labelText="Password"
          placeholder="Enter password..."
        />
      </FormGroup>
        <Button type="submit" on:click = {getdetails}>Submit
        
      </Button>
    
      
    </FluidForm>
</Modal>
</div>
<style>
.signup{
    display: flex;
    justify-content: center;
    font-size: 5rem;
    color:cornflowerblue;
    font-weight: 800;
    position: absolute;
    top:80px;
    left:40%;
    
}
.my{
  position: absolute;
  top:30%;
  left:43%;
  right:50%;
  bottom: 50%;
   
}
h3{
    left: 20px;
    font-weight: 500;
}
</style>

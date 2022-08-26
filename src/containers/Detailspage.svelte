<script>
      import { DataTable, Button } from "carbon-components-svelte";
      function clear(){
    window.localStorage.clear();
    window.reload();
  }
      
</script>
<div class="box">
  <h1>THANK U FOR LOGGING US....<br>Here are the details!!!!</h1>

<DataTable
  headers={[
    { key: "name", value: "name" },
    { key: "email", value: "email" },
    { key: "mobile", value: "mobile" },
    { key: "profession", value: "profession" },
    { key: "password", value: "password" },
  ]} 
  rows = {
   JSON.parse(window.localStorage.getItem("signupinfo"))
  }
  >
 
</DataTable>
<div class = "space">
<Button expressive kind="danger" on:click = {clear}>Logout</Button>
</div>
</div>
<style>
    .box{
        box-sizing: border-box;
        box-shadow: 10px 10px rgb(79, 247, 239);
        width:80vw;
        height:auto;
        position: fixed;
margin-top:100px;
margin-left: 180px;
    }
    .space{
        padding:20px;
        justify-content: center;
        display: flex;
    }
    h1{
      color:crimson;
      font-weight: 900;
      display: flex;
    justify-content: center;
    padding: 30px;
    }
</style>

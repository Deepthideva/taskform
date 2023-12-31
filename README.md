# taskform


<!DOCTYPE html>
<html lang="en">
<head>
	<link rel="stylesheet" href="deep.css">
	<script src="app.js" defer></script>
    <title>
        Form validation using HTML and JavaScript
    </title>
	
</head>
 
<body>
    <h1 style="text-align: center;" 
        REGISTRATION FORM
    </h1>
    <form name="RegForm" onsubmit="return GEEKFORGEEKS()"
          method="post">
        <p>
            Name:
            <input type="text" size="65" name="Name" />
        </p>
        <br />
        <p>
            Password:
            <input type="text" size="65" name="Password" />
        </p>
r
        <br />
<p> phone number:
	<input type="text" size="65" name="phone number"/>
</p>
<br/>
            <p>
            Select your course 
            <select type="text" value="" name="Subject">
                <option>BTECH</option>
                <option>BBA</option>
                <option>BCA</option>
                <option>B.COM</option>
                <option>MTECH</option>
		<option>MBA</option>
                <option>MED</option>
                <option>MCA</option>
                <option>M.COM</option>
                <option>OTHER</option>
            </select>
        </p>
        <br />
        <br />
        <p>
            Comments:
            <textarea cols="55" name="Comment"> </textarea>
        </p>
        <p>
            <input type="submit" value="send" name="Submit" />
            <input type="reset" value="Reset" name="Reset" />
        </p>
    </form>
</body>
</html>
            const form = document.querySelector('#form')
const username = document.querySelector('#username');
const email = document.querySelector('#email');
const password = document.querySelector('#password');
const cpassword = document.querySelector('#cpassword');

form.addEventListener('submit',(e)=>{
    
    if(!validateInputs()){
        e.preventDefault();
    }
})

function validateInputs(){
    const usernameVal = username.value.trim()
    const emailVal = email.value.trim();
    const passwordVal = password.value.trim();
    const cpasswordVal = cpassword.value.trim();
    let success = true

    if(usernameVal===''){
        success=false;
        setError(username,'Username is required')
    }
    else{
        setSuccess(username)
    }

    if(emailVal===''){
        success = false;
        setError(email,'Email is required')
    }
    else if(!validateEmail(emailVal)){
        success = false;
        setError(email,'Please enter a valid email')
    }
    else{
        setSuccess(email)
    }

    if(passwordVal === ''){
        success= false;
        setError(password,'Password is required')
    }
    else if(passwordVal.length<8){
        success = false;
        setError(password,'Password must be atleast 8 characters long')
    }
    else{
        setSuccess(password)
    }

    if(cpasswordVal === ''){
        success = false;
        setError(cpassword,'Confirm password is required')
    }
    else if(cpasswordVal!==passwordVal){
        success = false;
        setError(cpassword,'Password does not match')
    }
    else{
        setSuccess(cpassword)
    }

    return success;

}
//element - password, msg- pwd is reqd
function setError(element,message){
    const inputGroup = element.parentElement;
    const errorElement = inputGroup.querySelector('.error')

    errorElement.innerText = message;
    inputGroup.classList.add('error')
    inputGroup.classList.remove('success')
}

function setSuccess(element){
    const inputGroup = element.parentElement;
    const errorElement = inputGroup.querySelector('.error')

    errorElement.innerText = '';
    inputGroup.classList.add('success')
    inputGroup.classList.remove('error')
}

const validateEmail = (email) => {
    return String(email)
      .toLowerCase()
      .match(
        /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
      );
  };
  body{
    background: rgb(34,193,195);
    background: linear-gradient(0deg, rgba(34,193,195,1) 0%, rgba(121,32,153,1) 86%);
    background-attachment: fixed;
    margin:0;
    font-family: 'Poppins', sans-serif; 
}


}

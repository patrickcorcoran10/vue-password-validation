<template>
    <div class="form">
        <p :class="{ buttonRed : badPassword, buttonGreen : goodPassword }">Password</p>
        <input :class="{red : badPassword, green : goodPassword}" type="text" v-model="passwordInput" ref="passwordField" v-on:keyup="click">
        <br>
        <button @click="submit" :class="{ buttonRed : badPassword, buttonGreen : goodPassword }">Test Password</button>
    </div>
</template>

<script>
const upperCase = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z"];
const lowerCase = ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"];
const specialChars = ['!', '@','#','$','%','^','&','*',')','(','+','=','.','_','-'];
let passwordRequirements = {
    lowerCase: false,
    upperCase: false,
    specialChar: false,
    length: false,
    password: false,

}
function hasLowerCase(str) {
    for (var i = 0; i <= str.length; i ++) {
        lowerCase.forEach(letter => {
            if (str[i] === letter) {
                passwordRequirements.lowerCase = true
            } 
        })
    }
}
function hasUpperCase(str) {
    let arr = str.split("");
    console.log(arr)
        arr.forEach(letter => {
            console.log(letter)
            upperCase.forEach(ltr => {
                if (letter === ltr) {
                    passwordRequirements.upperCase = true;
                }
            })
        })
}
function hasSpecialChar(str) {
    let arr = str.split("");
    console.log(arr)
        arr.forEach(letter => {
            console.log(letter)
            specialChars.forEach(ltr => {
                if (letter === ltr) {
                    passwordRequirements.specialChar = true;
                }
            })
        })
}
export default {
    name: "Password Input",
    data() {
        return {
            passwordInput: "",
            badPassword: true,
            goodPassword: false
        }
    },
    methods: {
        click() {
            if (this.passwordInput.length >= 5) {
                passwordRequirements.length = true;
                this.badPassword = false;
                this.goodPassword = true;
            } else if (this.passwordInput.length > 11) {
                passwordRequirements.length = false;
                this.badPassword = true;
                this.goodPassword = false;
            }
            else if (this.passwordInput.includes("password") === true){
                console.log("not there")
                this.badPassword = true
                this.goodPassword = false
            }
            
             hasLowerCase(this.passwordInput)
             hasUpperCase(this.passwordInput)
             hasSpecialChar(this.passwordInput)

        }, 
        submit() {
           

            console.log(passwordRequirements)
            if (passwordRequirements.upperCase === true && passwordRequirements.lowerCase === true && passwordRequirements.specialChar === true && passwordRequirements.length === true && passwordRequirements.password === false) {
                alert("success")
            } else {
                alert("failure")
            }
            // reset our requirements obj.
            passwordRequirements = {
                lowerCase: false,
                upperCase: false,
                specialChar: false,
                length: false,
                password: false,

            }
            // Clear the input field
            this.passwordInput = "";
            this.badPassword = true;
            this.goodPassword = false
        }  
    }
}
</script>

<style scoped>
    .buttonRed {
        color: red;
    }
    .red:focus {
        border-color: red;
        border-radius: 4px;
        background-color: red;
    }
    .form {
        padding: 12px 20px;
        margin: 20px;
    }
    .buttonGreen {
        color: green
    }
    .green:focus {
        border-color: green;
        border-radius: 4px;
        background-color: green;
    }
</style>
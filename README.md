# Saylani-Object-Assignment

// Q1
// var itemsArray = [
//     { name: "colddrink", price: "60", quantity: "4" },
//     { name: "lays", price: "20", quantity: "11" },
//     { name: "jacket", price: "1200", quantity: "2" },
//     { name: "pen", price: "20", quantity: "8" }
// ];

// var total = 0;
// for (var i = 0; i < itemsArray.length; i++) {
//     var result = `Total price of ${itemsArray[i].name} is : ${itemsArray[i].price * itemsArray[i].quantity}`
//     console.log(result)
//     total += (+itemsArray[i].price) * (itemsArray[i].quantity)
// }
// console.log(`Total price of all items: ${total}`)


 // Q2
// var obj1 = {
//     name: "owais",
//     email: "mo417412@gmail.com",
//     password: "12345",
//     age: 19,
//     gender: "male",
//     city: "karachi",
//     country: "pakistan"
// }

// var find = prompt("find property in object");
// if (obj1.hasOwnProperty(find)) {
//     console.log(`${find} property found in object`)
// } else {
//     console.log(`${find} property not found in object`)

// }   

// Q3

// function Userdata(userName,email,password){
//     this.userName = userName;
//     this.email = email;
//     this.password = password;
// }

// var InputUser = document.getElementById("InputUser");
// var InputEmail = document.getElementById("InputEmail");
// var InputPassword1 = document.getElementById("InputPassword1");
// var signUp = document.getElementById("signUp");

// var objArr = []

// signUp.addEventListener('click',function(){
//     var userdata1 = new Userdata(InputUser.value,InputEmail.value,InputPassword1.value)
//     objArr.push(userdata1)
//     console.log(objArr);
// })

// Q4

function ChkPopulation(name, gender, address, qualification, profession) {
    this.name = name;
    this.gender = gender;
    this.address = address;
    this.qualification = qualification;
    this.profession = profession;

}

var InputUser = document.getElementById("InputUser");
var chkGender = document.getElementsByClassName("chkGender");
var inputAddress = document.getElementById("inputAddress");
var qualiSelect = document.getElementById("qualiSelect");
var profeSelect = document.getElementById("profeSelect");
var submit = document.getElementById("submit");
var tableBody = document.getElementById("tableBody");

var gend = "";

submit.addEventListener('click', function () {
    for (var i = 0; i < chkGender.length; i++) {
        if (chkGender[i].checked) {
            gend = chkGender[i].value;

        }
    }

    var qualiResult = qualiSelect.options[qualiSelect.selectedIndex].text;
    var professResult = profeSelect.options[profeSelect.selectedIndex].text;

    var userInputData = new ChkPopulation(InputUser.value, gend, inputAddress.value, qualiResult, professResult);

var getFromLocal = localStorage.getItem("userData");
// getFromLocal = JSON.parse(getFromLocal)
if(getFromLocal === null){

    var userObjj = []
}else{
    var getArryLocal = localStorage.getItem("userData");
    userObjj = JSON.parse(getFromLocal)
}

    userObjj.push(userInputData)

    localStorage.setItem('userData', JSON.stringify(userObjj))
    // *** reseting the valu after submitted *******
    InputUser.value = ""
    inputAddress.value = ""
    qualiSelect.selectedIndex = 0;
    profeSelect.selectedIndex = 0;

    // var getFromLocal = JSON.parse(localStorage.getItem('userobject'))

    // console.log(getFromLocal)
    displayData()

})

function displayData() {
    var getFromLocal = localStorage.getItem('userData');
    getFromLocal = JSON.parse(getFromLocal)
    console.log(getFromLocal)
    tableBody.innerHTML = ""
    for (var i = 0; i < getFromLocal.length; i++) {
        tableBody.innerHTML += `<tr>
    <th scope="row">${i + 1}</th>
    <td>${getFromLocal[i].name}</td>
    <td>${getFromLocal[i].gender}</td>
    <td>${getFromLocal[i].address}</td>
    <td>${getFromLocal[i].qualification}</td>
    <td>${getFromLocal[i].profession}</td>
    </tr>`
}
}

// <td><button onclick="deleteFunc(this)" class="btn-primary">Delete</button></td>
// function deleteFunc(btn){
//     btn.parentNode.parentNode.remove();
// }
displayData()

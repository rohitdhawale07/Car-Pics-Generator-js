# Car-Pics-Generator-js
## Hosted Link :- https://rohitdhawale07.github.io/Car-Pics-Generator-js/

This web page is simpley generating random images of car when we click on button.

## HTML Code
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>car Pics Generator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Car Pics Generator</h1>
        <button class="btn" id="btn">Get car</button>
        <div class="car-container">
            <img class="car-img" src="https://c.files.bbci.co.uk/F382/production/_123883326_852a3a31-69d7-4849-81c7-8087bf630251.jpg">
            <h3 class="car-name">car Name</h3>
        </div>
    </div>
    <script src="index.js"></script>
</body>
</html>
```
## CSS Code
```
body{
    margin: 0;
    display: flex;
    width: 100vw;
    height: 100vh;
    justify-content: center;
    background-color: rgb(184, 252, 157);
    align-items: center;
    font-family: cursive;
}

.container{
    background: aliceblue;
    border-radius: 10px;
    box-shadow: 0 10px 20px rgba(0,0,0,0.3);
    text-align: center;
    padding: 10px;
    width: 500px;
    margin: 5px;
}
.container h1{
    color: brown;
}

.btn{
    background-color: rgb(110, 154, 247);
    color: aliceblue;
    padding: 10px 30px;
    font-size: 16px;
    margin-bottom: 30px;
    border-radius: 6px;
    cursor: pointer;

}

.btn:disabled{
    background-color: gray;
    cursor: not-allowed;
}

.car-img{
    height: 300px;
    width: 300px;
    border-radius:10px;
    border: 3px solid rgb(84, 117, 84);
}

.car-name{
    margin: 20px;
    background-color: black;
    color: aliceblue;
    padding: 10px;
    border-radius: 6px;
    font-size: 17px;
    font-weight: 600;
    width: auto;
}

.car-container{
    display: none;
}
```
## JAVASCRIPT code
```
const btn = document.getElementById("btn");
const carContainer = document.querySelector(".car-container");
const carImg = document.querySelector(".car-img");
const carName = document.querySelector(".car-name");

btn.addEventListener("click", async function () {
  try {
    carImg.src = "spinner.svg";
    const response = await fetch("https://api.unsplash.com/photos/random?client_id=l-zyJUP_MBJp0tVerpIX4qs4B7M5EIkqecLKf4W8TO8&query=car");
    const data = await response.json();
    btn.innerText = "Get Cars";
    carContainer.style.display = "block";
    carImg.src = data.links.download;
    carName.innerText = data.alt_description;
  } catch (error) {
    console.log(error);
    btn.disabled = false;
    btn.innerText = "Get car";
    carName.innerText = "An error happened, please try again";
  }
});
```

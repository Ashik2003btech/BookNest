# BookNest 📚

BookNest is a simple and stylish web application for managing a virtual collection of books. Users can add books with a title, author, and description, as well as delete books from their collection.

## Features ✨
- Add books with a title, author, and short description.
- View added books in a responsive layout.
- Delete books when they are no longer needed.
- Stylish design with user-friendly interactions.


## Installation 🚀

1. Clone this repository:
   ```bash
   git clone https://github.com/Ashik2003btech/BookNest.git

## HTML Code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BookNest</title>
    <link rel="stylesheet" href="style.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins&display=swap" rel="stylesheet">
</head>
<body>
    <div class="navbar">
        <h1>BookNest</h1>
    </div>
    <div class="container">
        <div class="book-container">
            <h2>Rich Dad Poor Dad</h2>
            <h5>Robert Kiyosaki</h5>
            <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Vel sint amet repellat? Ipsam deserunt sed quibusdam consequuntur magni, laudantium officia.</p>
            <button onclick="deletebook(event)">Delete</button>
        </div>
    </div>
    <div class="popup-overlay"></div>
    <div class="popup-box">
        <h2>Add Book</h2>
        <form>
            <input type="text" placeholder="Book Title" id="book-title-input" required>
            <input type="text" placeholder="Book Author" id="book-author-input" required>
            <textarea placeholder="Short Description" id="book-description-input" required></textarea>
            <button id="add-book">Add</button>
            <button id="cancel-popup">Cancel</button>
        </form>
    </div>
    <button class="add-button" id="add-popup-button">+</button>
    <script src="script.js"></script>
</body>
</html>

##css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: "Poppins", sans-serif;
}

.navbar {
    background-color: #FD6569;
    padding: 10px;
}

.container {
    padding: 10px;
}

.book-container {
    display: inline-block;
    padding: 15px;
    width: 25%;
    border-radius: 10px;
    color: white;
    background-color: black;
    margin: 30px;
    vertical-align: top;
}

.book-container h2 {
    color: #FD6569;
}

.book-container button {
    background-color: #FD6569;
    color: black;
    border-radius: 10px;
    padding: 5px 10px;
    border: none;
    margin-top: 10px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.book-container button:hover {
    background-color: #FF7B7E;
}

.add-button {
    color: black;
    border-radius: 100%;
    background-color: #FD6569;
    padding: 20px 30px;
    font-size: 40px;
    border: none;
    position: fixed;
    bottom: 30px;
    right: 30px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.add-button:hover {
    background-color: #FF7B7E;
}

.popup-overlay {
    background-color: black;
    opacity: 0.8;
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    display: none;
    z-index: 1;
}

.popup-box {
    background-color: #FD6569;
    width: 40%;
    padding: 40px;
    border-radius: 10px;
    position: absolute;
    top: 20%;
    left: 30%;
    display: none;
    z-index: 2;
}

.popup-box input,
.popup-box textarea {
    background: transparent;
    border: none;
    width: 100%;
    margin: 5px 0;
    padding: 5px;
    font-size: 16px;
    border-bottom: 2px solid black;
}

.popup-box input:focus,
.popup-box textarea:focus {
    outline: none;
    border-bottom: 2px solid white;
}

.popup-box button {
    background-color: black;
    padding: 10px 20px;
    border: none;
    color: white;
    margin: 5px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.popup-box button:hover {
    background-color: white;
    color: black;
}


##Java Script
// Selecting popup box elements
var popupoverlay = document.querySelector(".popup-overlay");
var popupbox = document.querySelector(".popup-box");
var addpopupbutton = document.getElementById("add-popup-button");

addpopupbutton.addEventListener("click", function () {
    popupoverlay.style.display = "block";
    popupbox.style.display = "block";
});

// Selecting cancel button
var cancelpopup = document.getElementById("cancel-popup");
cancelpopup.addEventListener("click", function (event) {
    event.preventDefault();
    popupoverlay.style.display = "none";
    popupbox.style.display = "none";
});

// Adding new books
var container = document.querySelector(".container");
var addbook = document.getElementById("add-book");
var booktitleinput = document.getElementById("book-title-input");
var bookauthorinput = document.getElementById("book-author-input");
var bookdescriptioninput = document.getElementById("book-description-input");

addbook.addEventListener("click", function (event) {
    event.preventDefault();

    if (
        booktitleinput.value.trim() === "" ||
        bookauthorinput.value.trim() === "" ||
        bookdescriptioninput.value.trim() === ""
    ) {
        alert("Please fill in all fields.");
        return;
    }

    var div = document.createElement("div");
    div.setAttribute("class", "book-container");
    div.innerHTML = `
        <h2>${booktitleinput.value}</h2>
        <h5>${bookauthorinput.value}</h5>
        <p>${bookdescriptioninput.value}</p>
        <button onclick="deletebook(event)">Delete</button>
    `;

    container.append(div);

    // Clear inputs and hide popup
    booktitleinput.value = "";
    bookauthorinput.value = "";
    bookdescriptioninput.value = "";
    popupoverlay.style.display = "none";
    popupbox.style.display = "none";
});

// Delete book
function deletebook(event) {
    const book = event.target.parentElement;
    if (book) {
        book.remove();
    }
}





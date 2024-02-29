# SPACE// index.js

const express = require('express');
const bodyParser = require('body-parser');

const app = express();
const PORT = 3000; // You can change the port if needed

// Middleware
app.use(bodyParser.urlencoded({ extended: false }));
app.use(bodyParser.json());

// Dummy database (in a real-world app, you'd use a real database like MongoDB)
let clothes = [
    { id: 1, name: 'T-shirt', price: 20 },
    { id: 2, name: 'Jeans', price: 50 },
    { id: 3, name: 'Dress', price: 80 }
];

// Routes
app.get('/clothes', (req, res) => {
    res.json(clothes);
});

app.post('/clothes', (req, res) => {
    const { name, price } = req.body;
    const id = clothes.length + 1;
    const newCloth = { id, name, price };
    clothes.push(newCloth);
    res.status(201).json(newCloth);
});

app.listen(PORT, () => {
    console.log(`Server is running on http://localhost:${PORT}`);
});

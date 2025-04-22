const express = require('express');
const cors = require('cors');

const app = express();
app.use(cors());

// Mock user purchase history and product recommendations
const userPurchases = {
    "user1": ["Laptop", "Mouse", "Keyboard"],
    "user2": ["Shoes", "T-Shirt", "Jeans"]
};

const productRecommendations = {
    "Laptop": ["Laptop Bag", "Cooling Pad", "External Hard Drive"],
    "Mouse": ["Mouse Pad", "Wireless Charger"],
    "Keyboard": ["Mechanical Keycaps", "RGB Light Strip"],
    "Shoes": ["Socks", "Shoe Polish"],
    "T-Shirt": ["Jacket", "Cap"],
    "Jeans": ["Belt", "Wallet"]
};

app.get('/recommend', (req, res) => {
    const userId = req.query.user_id;
    if (!userPurchases[userId]) {
        return res.status(404).json({ error: "User not found" });
    }

    const pastPurchases = userPurchases[userId];
    const recommendations = new Set();
    
    pastPurchases.forEach(item => {
        if (productRecommendations[item]) {
            productRecommendations[item].forEach(recommendation => recommendations.add(recommendation));
        }
    });

    res.json({ user_id: userId, recommendations: Array.from(recommendations) });
});

const PORT = 5000;
app.listen(PORT, () => {
    console.log(`Server running on http://localhost:${PORT}`);
});
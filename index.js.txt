let cart = [];
let total = 0;

// Add event listeners to all Add to Cart buttons
document.querySelectorAll('.addToCart').forEach(button => {
    button.addEventListener('click', () => {
        const productName = button.getAttribute('data-name');
        const productPrice = parseFloat(button.getAttribute('data-price'));

        // Add the product to the cart
        cart.push({ name: productName, price: productPrice });
        total += productPrice;

        // Update the cart display
        updateCartDisplay();
    });
});

function updateCartDisplay() {
    const cartItems = document.getElementById('cartItems');
    const totalPrice = document.getElementById('totalPrice');

    // Clear the current cart display
    cartItems.innerHTML = '';

    // Add each item in the cart to the display
    cart.forEach(item => {
        const li = document.createElement('li');
        li.textContent = `${item.name} - $${item.price}`;
        cartItems.appendChild(li);
    });

    // Update the total price
    totalPrice.textContent = `Total: $${total.toFixed(2)}`;
}

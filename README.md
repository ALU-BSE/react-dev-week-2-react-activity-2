# react-dev-week-2-react-activity-2

**Project Goal:** Create a simple React application that displays a list of product cards. Each product card will show the product's name, price, and image. Users should be able to add new products dynamically.

**Tools:**

*   **Vite:** For fast development and build.
*   **React:** For building the UI.
*   **TypeScript:** For type safety and better code organization.

**Steps:**

**Phase 1: Project Setup with Vite**

1.  **Initialize the project:**

    *   Open your terminal and run:
        ```bash
        npm create vite@latest product-card-app
        ```
    *   Choose `react` as the framework and `typescript` as the variant.
    *   Navigate to the project directory:
        ```bash
        cd product-card-app
        ```
    *   Install dependencies:
        ```bash
        npm install
        ```

2.  **Run the Development Server:**

    ```bash
    npm run dev
    ```
    This will start the development server. You should see the default Vite + React welcome page in your browser.

**Phase 2: Creating the Product Card Component (TypeScript)**

1.  **Create a new component file:**

    *   Inside the `src` directory, create a new folder called `components`.
    *   Inside `components`, create a new file named `ProductCard.tsx`.

2.  **Define the `Product` type:**

    *   At the top of `ProductCard.tsx`, define a TypeScript interface for the product data:

    ```typescript
    interface Product {
      name: string;
      price: number;
      imageUrl: string;
    }
    ```

3.  **Create the `ProductCard` component:**

    ```typescript
    import React from 'react';

    interface Product {
      name: string;
      price: number;
      imageUrl: string;
    }

    interface ProductCardProps {
      product: Product;
    }

    const ProductCard: React.FC<ProductCardProps> = ({ product }) => {
      return (
        <div className="product-card">
          <img src={product.imageUrl} alt={product.name} />
          <h3>{product.name}</h3>
          <p>${product.price.toFixed(2)}</p>
        </div>
      );
    };

    export default ProductCard;
    ```

    *   **Explanation:**
        *   We import React.
        *   We define an interface `ProductCardProps` to specify that this component expects a `product` prop of type `Product`.
        *   The `ProductCard` component is a functional component that receives the `product` prop.
        *   It renders the product information using JSX.
        *   We use basic inline styling for now (you can improve this later with CSS modules or a CSS framework).

**Phase 3: Using the Product Card in `App.tsx`**

1.  **Modify `App.tsx`:**

    *   Replace the contents of `src/App.tsx` with the following:

    ```typescript
    import React, { useState } from 'react';
    import ProductCard from './components/ProductCard';
    import './App.css'; // Import the CSS file

    interface Product {
        name: string;
        price: number;
        imageUrl: string;
    }

    const App: React.FC = () => {
      const [products, setProducts] = useState<Product[]>([
        {
          name: 'Example Product 1',
          price: 19.99,
          imageUrl: 'https://via.placeholder.com/150', // Placeholder image
        },
        {
          name: 'Example Product 2',
          price: 29.99,
          imageUrl: 'https://via.placeholder.com/150',
        },
      ]);

      return (
        <div className="app">
          <h1>Product List</h1>
          <div className="product-list">
            {products.map((product, index) => (
              <ProductCard key={index} product={product} />
            ))}
          </div>
        </div>
      );
    };

    export default App;
    ```

    *   **Explanation:**
        *   We import `useState` from React, `ProductCard` from our component, and also import `App.css` (we'll create it in the next step).
        *   We define the Product type again here.
        *   `useState` is used to manage the `products` state, initialized with an array of sample products.
        *   `products.map` iterates through the products array to render a `ProductCard` for each product.
        *   The `key` prop is important for React to efficiently update the list.

**Phase 4: Basic Styling (App.css)**

1.  **Create `App.css`:**

    *   In the `src` directory, create a new file named `App.css`.
2.  **Add some styles:**

    ```css
    .app {
      text-align: center;
      padding: 20px;
    }

    .product-list {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
    }

    .product-card {
      border: 1px solid #ccc;
      padding: 15px;
      width: 200px;
    }

    .product-card img {
      max-width: 100%;
      height: auto;
    }
    ```

**Phase 5: Adding New Products (State)**

1.  **Add a form to `App.tsx`:**

    ```typescript
    // ... (other imports)
    import { useState } from 'react';

    // ... (Product interface)

    const App: React.FC = () => {
      // ... (products state)

      const [newProductName, setNewProductName] = useState('');
      const [newProductPrice, setNewProductPrice] = useState(0);
      const [newProductImageUrl, setNewProductImageUrl] = useState('');

      const handleAddProduct = () => {
        const newProduct: Product = {
          name: newProductName,
          price: newProductPrice,
          imageUrl: newProductImageUrl,
        };

        setProducts([...products, newProduct]);

        // Clear the input fields
        setNewProductName('');
        setNewProductPrice(0);
        setNewProductImageUrl('');
      };

      return (
        <div className="app">
          <h1>Product List</h1>

          {/* Add Product Form */}
          <div>
            <h2>Add New Product</h2>
            <input
              type="text"
              placeholder="Name"
              value={newProductName}
              onChange={(e) => setNewProductName(e.target.value)}
            />
            <input
              type="number"
              placeholder="Price"
              value={newProductPrice}
              onChange={(e) => setNewProductPrice(Number(e.target.value))}
            />
            <input
              type="text"
              placeholder="Image URL"
              value={newProductImageUrl}
              onChange={(e) => setNewProductImageUrl(e.target.value)}
            />
            <button onClick={handleAddProduct}>Add Product</button>
          </div>

          <div className="product-list">
            {/* ... (product mapping remains the same) */}
          </div>
        </div>
      );
    };

    export default App;
    ```

    *   **Explanation:**
        *   We add three new state variables using `useState`: `newProductName`, `newProductPrice`, and `newProductImageUrl` to store the values from the input fields.
        *   The `handleAddProduct` function:
            *   Creates a new `Product` object from the input field values.
            *   Uses the spread operator (`...products`) to create a new array that includes the existing products plus the new product. This updates the `products` state.
            *   Clears the input fields.
        *   We add a form with input fields and a button. The `onChange` event handlers update the state variables as the user types.

**Phase 6: Run and Test**

1.  **Save all files.**
2.  If your development server is not already running, start it:

    ```bash
    npm run dev
    ```
3.  Open your web browser and go to the URL provided by the development server (usually `http://localhost:5173/`).
4.  You should see the initial product cards. Try adding new products using the form.

**Further Challenges (Optional):**

*   **Improved Styling:** Use a CSS framework like Tailwind CSS or Material UI to make the app look more professional.
*   **Input Validation:** Add validation to ensure that users enter valid data in the form.
*   **Delete Products:** Add a button to each `ProductCard` to remove a product from the list.
*   **Edit Products:** Allow users to edit the details of existing products.
*   **Local Storage:** Store the products in local storage so they persist even after the browser is closed.

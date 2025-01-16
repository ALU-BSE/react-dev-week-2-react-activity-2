
**I. Basic Component Creation with TypeScript (15 Tasks)**

1.  **Set Up Project (TypeScript):** Create a new React project using `create-react-app` with the TypeScript template: `npx create-react-app my-app --template typescript` or using `Vite`: `npm create vite@latest my-app -- --template react-ts`
2.  **Run Development Server:** Start the development server to view your application in the browser.
3.  **Create a Component File:** Create a new file with a `.tsx` extension (e.g., `MyComponent.tsx`) inside the `src` folder.
4.  **Functional Component (Typed):** Write a basic functional component, explicitly defining the return type as `JSX.Element`.
5.  **Import Component:** Import your component into the main `App` component file (`App.tsx`).
6.  **Render Component:** Render your component within the `App` component's JSX.
7.  **JSX Element:** Change the `<h1>` tag in your component to a different JSX element, ensuring type safety.
8.  **Multiple Elements:** Return multiple JSX elements, wrapping them in a single parent element or using a React Fragment (`<> </>`).
9.  **Nested Component:** Create another new component (e.g., `InnerComponent.tsx`) and render it inside your first component.
10. **Component with Props (Typed):** Define an interface for your component's props (e.g., `interface MyComponentProps { name: string; }`).
11. **Display Prop:** Display the value of the `name` prop within your component's JSX, utilizing type safety.
12. **Pass Prop:** Pass a value for the `name` prop when rendering your component in `App.tsx`, ensuring the value is of the correct type.
13. **Multiple Props (Typed):** Add more props to your component's interface and use them in the JSX, maintaining type safety.
14. **Default Props:** Set default values for props using either the default props pattern or default parameters in the function definition.
15. **Optional Props:** Define some props as optional in your interface using the `?` modifier.

**II. Styling Components (15 Tasks)**

*(These tasks remain largely the same as the styling concepts are not directly affected by TypeScript. However, you can enforce type safety when working with inline styles or CSS Modules using TypeScript.)*

16. **Inline Styles (Typed):** Add inline styles using the `style` attribute. Use an interface for better type checking:
17. **External CSS:** Create a separate CSS file (e.g., `MyComponent.css`) and import it into your component.
18. **Class Names:** Add `className` attributes to JSX elements.
19. **CSS Selectors:** Define CSS rules in your external CSS file.
20. **Multiple Classes:** Apply multiple CSS classes to elements.
21. **Dynamic Classes:** Use template literals to conditionally apply classes based on props or state, maintaining type safety.
22. **CSS Modules:** Set up CSS Modules (if not already configured).
23. **CSS Modules Import (Typed):** Import CSS Modules with type definitions (create a `*.module.css.d.ts` file to describe the shape of the CSS Modules object).
24. **CSS Framework (Optional):** Install a CSS framework and use its utility classes.
25. **Styled Components (Optional):** Install `styled-components` and its type definitions: `npm install styled-components @types/styled-components`.
26. **Styled Components Syntax:** Define styles using tagged template literals in `styled-components`.
27. **Props in Styled Components (Typed):** Pass props and use them to dynamically adjust styles, using interfaces to type the props.
28. **Component-Specific Styling:** Create different CSS files for different components.
29. **Global Styles:** Define global styles in your main CSS file.
30. **Responsive Design:** Use media queries in your CSS to adapt to different screen sizes.

**III. React State with TypeScript (15 Tasks)**

31. **useState Hook (Typed):** Import the `useState` hook and use it with type parameters:
32. **Initialize State:** Initialize the state variable with a default value of the correct type.
33. **Display State:** Display the value of the state variable in your JSX.
34. **Update State:** Create a button and attach an `onClick` event handler.
35. **Event Handler Function (Typed):** Define the event handler function with the correct type for the event (e.g., `React.MouseEvent<HTMLButtonElement>`).
36. **Functional Updates:** Use the functional form of `setState` to update state based on the previous state.
37. **Multiple State Variables (Typed):** Use `useState` multiple times, providing appropriate type parameters for each state variable.
38. **Object State (Typed):** Define an interface for your object state and use it with `useState`:
39. **Array State (Typed):** Use `useState` with an array type:
    ```typescript
    const [items, setItems] = useState<string[]>([]); // State is an array of strings
    ```
40. **Conditional Rendering:** Use state to conditionally render JSX elements, ensuring type safety.
41. **Controlled Input (Typed):** Use state to manage the value of an input field, typing the `onChange` event handler appropriately (e.g., `React.ChangeEvent<HTMLInputElement>`).
42. **Form Submission (Typed):** Handle form submission, typing the event as `React.FormEvent<HTMLFormElement>`. Prevent default behavior with `event.preventDefault()`.
43. **Lifting State Up:** Move state from a child to a parent component, maintaining type safety in both components.
44. **Passing State Down (Typed):** Pass state and setter functions as props, defining the prop types in the child component's interface.
45. **Context API (Optional):** Explore using the Context API for global state management with TypeScript. Define the context value type using an interface.

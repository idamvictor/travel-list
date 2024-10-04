# 🧳 Packing List App

## Overview

This is a **React** project designed to help users create and manage their packing lists efficiently. Users can add items, specify quantities, mark items as packed, sort by various categories, and clear the list. The app provides an intuitive and interactive interface for users to ensure they are prepared for their trips.

## Features

- **Add Items:** Users can input item descriptions and quantities, which are then dynamically added to the list.
- **Mark as Packed:** Users can mark items as packed or unpacked by checking a box next to each item.
- **Sorting Options:** Items can be sorted by input order, description, or packed status.
- **Delete Items:** Users can remove individual items from the list.
- **Clear All Items:** Users can clear the entire list with a single button.
- **Responsive Design:** The app is responsive and adapts well to different screen sizes.
  
## Tech Stack

- **React** (with Hooks)
- **CSS** (custom styling with grid layout for responsive design)
- **JavaScript** (for dynamic state handling and functionality)

## Demo

![App Screenshot](link-to-your-screenshot)

## Getting Started

### Prerequisites

Ensure you have **Node.js** installed on your machine. You can download it from [here](https://nodejs.org/en/).

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/packing-list-app.git
   ```

2. Navigate into the project directory:
   ```bash
   cd packing-list-app
   ```

3. Install the dependencies:
   ```bash
   npm install
   ```

4. Run the application:
   ```bash
   npm start
   ```

   The app will be available at `http://localhost:3000` in your browser.

## Project Structure

```
├── public
│   ├── index.html
├── src
│   ├── components
│   │   ├── App.js          # Main app component
│   │   ├── Form.js         # Form to add items
│   │   ├── PackingList.js  # List display with sorting options
│   │   ├── Item.js         # Individual list item component
│   │   ├── Stats.js        # Stats display for packed percentage
│   ├── index.js            # ReactDOM entry point
│   ├── index.css           # Main styling
└── package.json
```

### Key Components

1. **App.js**
   - The main component that manages the state for the entire app. It handles adding, deleting, and toggling items.

2. **Form.js**
   - Allows users to input a description and quantity for items and submit them to the list. Uses `useState` to manage form state.

3. **PackingList.js**
   - Displays the list of items. Provides sorting options and the ability to clear the entire list.

4. **Item.js**
   - Represents a single item in the packing list. Includes a checkbox to mark items as packed or unpacked, and a delete button.

5. **Stats.js**
   - Displays statistics based on the list, such as the total number of items and the percentage of items that have been packed.

## CSS Styling

- The project uses CSS Grid and Flexbox for layout design, ensuring responsiveness across different screen sizes.
- Fonts are imported from Google Fonts: `Monoton` for the logo and `Quicksand` for the rest of the text.
- Custom CSS transitions are applied to buttons for a smooth hover effect.

### Media Queries
- The app is designed to be responsive, and media queries have been implemented to adjust the layout for smaller screens.

```css
@media (max-width: 600px) {
  .list ul {
    grid-template-columns: 1fr;
  }

  h1 {
    font-size: 5rem;
  }
}
```

## State Management

This app uses React's `useState` hook to manage state for:
- **Items:** The list of items (description, quantity, packed status).
- **Form inputs:** The item description and quantity values.
- **Sorting:** Which sorting method to apply.

State updates are efficiently handled with the `setItems` function to ensure the UI updates in real-time when users add or modify list items.

### Adding Items

The `handleAddItems` function takes an object with the item description and quantity, then updates the list state:
```js
function handleAddItems(item) {
  setItems((items) => [...items, item]);
}
```

### Toggling Packed Status

The `handleToggleItem` function checks whether an item is packed or not and toggles the state:
```js
function handleToggleItem(id) {
  setItems((items) =>
    items.map((item) =>
      item.id === id ? { ...item, packed: !item.packed } : item
    )
  );
}
```

### Sorting

Users can sort the list by three different criteria:
1. Input Order
2. Description (alphabetically)
3. Packed Status (unpacked items first)

```js
if (sortBy === "description")
  sortedItems = items
    .slice()
    .sort((a, b) => a.description.localeCompare(b.description));

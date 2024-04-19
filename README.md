# Node-React Starter Project Guide

This README provides a guide on how to set up a starter project with a Node.js backend and a React frontend. This setup is suitable for developers looking to build full-stack JavaScript applications.

## Prerequisites

- Node.js and npm
- Basic knowledge of JavaScript and React

## Setting Up the Project

1. **Create the project directories:**
   - One for the backend and one for the frontend.
   ```bash
   mkdir myproject
   cd myproject
   mkdir backend
   mkdir frontend
   ```

2. **Set up the Node.js backend:**
   - Navigate to the backend directory and initialize a new Node.js project.
   ```bash
   cd backend
   npm init -y
   npm install express
   ```

   - Create a simple Express server.
   ```javascript
   const express = require('express');
   const app = express();

   app.get('/', (req, res) => {
       res.send('Hello from the backend!');
   });

   const PORT = process.env.PORT || 5000;
   app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
   ```

3. **Set up the React frontend:**
   - Navigate to the frontend directory and create a new React app.
   ```bash
   cd ../frontend
   npx create-react-app .
   ```

   - Modify the `App.js` to fetch data from the Express backend.
   ```javascript
   import React, { useEffect, useState } from 'react';
   import './App.css';

   function App() {
       const [data, setData] = useState('');

       useEffect(() => {
           fetch('http://localhost:5000/')
               .then(response => response.text())
               .then(data => setData(data));
       }, []);

       return (
           <div className="App">
               <header className="App-header">
                   <p>
                       {data}
                   </p>
               </header>
           </div>
       );
   }

   export default App;
   ```

4. **Run the applications:**
   - Start the Express server.
   ```bash
   # From the backend directory
   node server.js
   ```

   - Start the React app.
   ```bash
   # From the frontend directory
   npm start
   ```

## Conclusion

You now have a basic Node-React starter project set up. This configuration is a foundation for building full-stack JavaScript applications.

For more detailed information, visit the [Express documentation](https://expressjs.com/) and [React documentation](https://reactjs.org/).

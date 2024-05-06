# Protected Route

## Step 1 

create a ProtectedRoute.js file where u will write the main logic of the Protected Route 

    import React from 'react';
    import { Route, Navigate } from 'react-router-dom';
    
    const ProtectedRoute = ({ element: Element, ...rest }) => {
      const isLogin = localStorage.getItem('isLogin') === 'true';
      
      // If user is already logged in, redirect away from the login page
      if (isLogin) {
        return <Navigate to="/" replace />;
      }
    
      // Otherwise, render the specified element
      return <Element {...rest} />;
    };
    
    export default ProtectedRoute;


## Step 2

import ProtectedRoute in App.js and initilize it in route

    import ProtectedRoute from './Components/ProtectedRoute/ProtectedRoute';
    
    <Route path="/login" element={<ProtectedRoute element={LoginSignup} />} />

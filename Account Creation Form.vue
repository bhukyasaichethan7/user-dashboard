// AccountCreationForm.js
import React, { useState } from 'react';
import axios from 'axios';

const AccountCreationForm = () => {
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');

  const handleCreateAccount = () => {
    // Send the username and password to your API endpoint for account creation
    axios.post('your-api-endpoint/create-account', { username, password })
      .then(response => {
        console.log('Account created successfully:', response.data);
        // Optionally, you can reset the form after successful creation
        setUsername('');
        setPassword('');
      })
      .catch(error => console.error('Error creating account:', error));
  };

  return (
    <div>
      <label>Username:</label>
      <input
        type="text"
        value={username}
        onChange={(e) => setUsername(e.target.value)}
      />
      <label>Password:</label>
      <input
        type="password"
        value={password}
        onChange={(e) => setPassword(e.target.value)}
      />
      <button onClick={handleCreateAccount}>Create Account</button>
    </div>
  );
};

export default AccountCreationForm;


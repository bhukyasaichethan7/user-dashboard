// UserTable.js
import React, { useState, useEffect } from 'react';
import axios from 'axios';

const UserTable = () => {
  const [users, setUsers] = useState([]);
  const [searchTerm, setSearchTerm] = useState('');

  useEffect(() => {
    // Fetch user data from your API endpoint
    axios.get('your-api-endpoint/users')
      .then(response => setUsers(response.data))
      .catch(error => console.error('Error fetching user data:', error));
  }, []);

  const filteredUsers = users.filter(user =>
    user.username.toLowerCase().includes(searchTerm.toLowerCase())
  );

  return (
    <div>
      <input
        type="text"
        placeholder="Search by username"
        onChange={(e) => setSearchTerm(e.target.value)}
      />
      <table>
        <thead>
          <tr>
            <th>Username</th>
            <th>Email</th>
            {/* Add more columns as needed */}
          </tr>
        </thead>
        <tbody>
          {filteredUsers.map(user => (
            <tr key={user.id}>
              <td>{user.username}</td>
              <td>{user.email}</td>
              {/* Add more cells as needed */}
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
};

export default UserTable;


import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link, useParams } from 'react-router-dom';

// Simple styling object for navigation
const navStyle = {
  display: 'flex',
  gap: '15px',
  background: '#f4f4f4',
  padding: '10px',
  listStyle: 'none'
};

// Component Definitions
const Home = () => <h2>Home Page</h2>;
const About = () => <h2>About Page</h2>;
const Dashboard = () => <h2>Dashboard Page</h2>;

const UserProfile = () => {
  const { userId } = useParams();
  return (
    <div>
      <h2>User Profile</h2>
      <p>Displaying details for User ID: <strong>{userId}</strong></p>
    </div>
  );
};

const NotFound = () => (
  <div>
    <h2>404 - Not Found</h2>
    <p>The page you are looking for does not exist.</p>
    <Link to="/">Go Back Home</Link>
  </div>
);

function App() {
  return (
    <Router>
      <div>
        {/* Navigation Bar */}
        <nav>
          <ul style={navStyle}>
            <li><Link to="/">Home</Link></li>
            <li><Link to="/about">About</Link></li>
            <li><Link to="/dashboard">Dashboard</Link></li>
            <li><Link to="/user/123">User Profile (ID: 123)</Link></li>
            <li><Link to="/user/abc">User Profile (ID: abc)</Link></li>
          </ul>
        </nav>

        {/* Route Configuration */}
        <div style={{ padding: '20px' }}>
          <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/about" element={<About />} />
            <Route path="/dashboard" element={<Dashboard />} />
            <Route path="/user/:userId" element={<UserProfile />} />
            {/* Catch-all route for unmatched paths */}
            <Route path="*" element={<NotFound />} />
          </Routes>
        </div>
      </div>
    </Router>
  );
}

export default App;

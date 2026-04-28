First select “Network Access”  , Add IP Address button., Add 0.0.0.0/0 IP address 
Click New Repository. name to repository and select Create Repository. Leave description empty. 
 Railway web site
  Netlify web site 
  Make sure there are no spaces between
MONGO_URI=<uri>
server.js
dns.setDefaultResultOrder('ipv4first');

const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');
require('dotenv').config();

const app = express();
app.use(cors());
app.use(express.json());

mongoose.connect(process.env.MONGO_URI)
    .then(() => console.log('MongoDB connected'))
    .catch(err => console.log(err));

const itemRoutes = require('./routes/items');
app.use('/api/items', itemRoutes);

const PORT = process.env.PORT || 5001;
app.listen(PORT, () => console.log(`Server running on port 
${PORT}`));

In order to use Render we have to change a part of package. Json in the
back-end.
Add the "start": "node server.js", to the scripts. It is required by the Railway. 

railway> back-end as the root folder (settings)
--variables tab-- add the MONGO_URI variable. (Auto suggested)
Go to settings and generate a public domain--.
Copy the Domain, frontend In the .env file change the PORT to the copied one. **
Add it to the App.jsx > -- const API_URL = import.meta.env. VITE_API_URL | | 'http://localhost:5000/api';--(copy domain)
await axios.post('http://localhost:5000/api/items', formData); --> await axios.post('${API_URL}/api/items', formData);
axios.get(`${import.meta.env.VITE_APP_URL}/api/items`);
netlify
base d - frontend , build - npm run build , publish - frontend/dist, add key pair,  Add the VITE_APP_URL





# DevTinder

- Create a Vite + Raect application
- Remove unnecessary code and create a Hello World app
- Install Tailwind CSS
- Install Daisy UI
- Add Navbar component to App.jsx
- Create a NavBar.jsx separate component file
- Install react router dom
- Create BrowserRouter > Routes > Route=/ Body > RouteChildren
- Create an Outlet in your Body Component
- Create a footer
- Create a Login Page
- Install axios
- CORS - install cors in backend => add middleware to with configurations: origin, credentials: true
- Whenever you're making API call so pass axios => { withCredentials : true}
- Install react-redux + @redux/toolkit - https://redux-toolkit.js.org/tutorials/quick-start
- configureStore => Provider => createSLice => add reducer to store
- Add redux devtools in chrome
- Login and see if your data is coming properly in the store
- NavBar should update as soon as user logs in
- Refactor our code to add constants file + create a components folder
- You should not be access other routes without login
- If token is not present, redirect user to login page
- Logout Feature
- Get the feed and add the feed in the store
- build the user card on feed
- Edit Profile Feature
- Show Toast Message on save profile
- New Page - See all my connections
- New Page - See all my connection requests
- Feature - Accept/Reject Connection Request
- Send/ignore the user card from feed
- Signup New User
- E2ETesting

# Deployment

- Signup on AWS
- Launch instance
- chmod 400 <secret>.pem
- ssh -i "devTinder1.pem" ubuntu@ec2-13-51-47-44.eu-north-1.compute.amazonaws.com
- Install Node version 18.20.7
- Git clone
- Frontend
  - npm install -> depenedencies install
  - npm run build
  - sudo apt update
  - sudo apt install nginx
  - sudo systemctl start nginx
  - sudo systemctl enable nginx
  - Copy code from dist(build files) to /var/www/html/
  - sudo scp -r dist/\* /var/www/html/
  - Enable port :80 of your instance
- Backend
  - allowed ec2 instance public IP on mongodb server
  - npm install pm2 -g
  - pm2 start npm --name "devTinder-backend" -- start
  - pm2 logs
  - pm2 list, pm2 flush <name>, pm2 stop <name>, pm2 delete <name>
  - config nginx - /etc/nginx/sites-available/default
    location /api/ {  
    proxy_pass http://localhost:7777/;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
    }
  - restart nginxm - sudo systemctl restart nginx
  - Modify the BASEURL in frontend project to "/api"

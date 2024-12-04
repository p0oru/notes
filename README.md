To achieve your goals, follow these detailed steps for each task:

## Step 1: Create a Basic Ionic React Capacitor Application

1. **Install Ionic CLI**: Open your terminal and run:
   ```bash
   npm install -g @ionic/cli
   ```

2. **Create a New Ionic Project**: Use the Ionic CLI to create a new project with React and Capacitor:
   ```bash
   ionic start myApp blank --type=react --capacitor
   ```
   This will create a new Ionic project named `myApp`.

3. **Navigate to the Project Directory**:
   ```bash
   cd myApp
   ```

4. **Add Capacitor Plugins (Optional)**: If you need native functionality, you can add plugins like Camera, Filesystem, etc.:
   ```bash
   npm install @capacitor/camera @capacitor/preferences @capacitor/filesystem
   ```

5. **Run the Application**: Start the development server to see your app in action:
   ```bash
   ionic serve
   ```

## Step 2: Create a Basic Express Application

1. **Initialize a Node.js Project**: In your terminal, create a new directory for your Express app and initialize it:
   ```bash
   mkdir express-app
   cd express-app
   npm init -y
   ```

2. **Install Express**: Add Express to your project:
   ```bash
   npm install express
   ```

3. **Create the Server File**: Create a file named `server.js` and add the following code to set up a basic Express server:
   ```javascript
   const express = require('express');
   const app = express();

   app.get('/', (req, res) => {
     res.send('Hello World from Express!');
   });

   app.listen(3000, () => {
     console.log('Express server listening on port 3000');
   });
   ```

4. **Run the Server**: Start your Express server by running:
   ```bash
   node server.js
   ```
   Visit `http://localhost:3000` in your browser to see the message.

## Step 3: Create an SQL Database and Connect It

1. **Set Up MySQL Database**:
   
    - Open your MySQL client and log in using:
      ```bash
      mysql -u root -p
      ```
      Enter `1234` when prompted for the password.

    - Create a database named `vids`:
      ```sql
      CREATE DATABASE vids;
      ```

    - Use the `vids` database:
      ```sql
      USE vids;
      ```

    - Create a table named `videos` with columns for storing video information:
      ```sql
      CREATE TABLE videos (
        id INT AUTO_INCREMENT PRIMARY KEY,
        title VARCHAR(255) NOT NULL,
        url VARCHAR(255) NOT NULL,
        description TEXT
      );
      ```

    - Insert three random YouTube video entries into the `videos` table:
      ```sql
      INSERT INTO videos (title, url, description) VALUES 
      ('Video 1', 'https://youtube.com/watch?v=video1', 'Description for video 1'),
      ('Video 2', 'https://youtube.com/watch?v=video2', 'Description for video 2'),
      ('Video 3', 'https://youtube.com/watch?v=video3', 'Description for video 3');
      ```

2. **Connect Express App to MySQL**:

    - Install MySQL package in your Express app directory:
      ```bash
      npm install mysql
      ```

    - Modify `server.js` to connect to MySQL and fetch videos:

    ```javascript
    const express = require('express');
    const mysql = require('mysql');

    const app = express();

    // Create connection to MySQL database
    const db = mysql.createConnection({
      host: 'localhost',
      user: 'root',
      password: '1234',
      database: 'vids'
    });

    // Connect to database
    db.connect(err => {
      if (err) {
        throw err;
      }
      console.log('MySQL connected...');
    });

    // Route to fetch videos from database
    app.get('/videos', (req, res) => {
      let sql = 'SELECT * FROM videos';
      db.query(sql, (err, results) => {
        if (err) throw err;
        res.json(results);
      });
    });

    app.listen(3000, () => {
      console.log('Server running on port 3000');
    });
    ```

3. **Test Your Setup**:

    - Run the Express server again using `node server.js`.
    
    - Visit `http://localhost:3000/videos` in your browser to see the list of YouTube videos fetched from your MySQL database.

These steps will guide you through setting up an Ionic React application with Capacitor, creating an Express backend, and integrating it with a MySQL database to display data on localhost.

Citations:
[1] https://ionicframework.com/docs/react/your-first-app
[2] https://youteam.io/blog/how-to-build-ionic-apps/
[3] https://daily.dev/blog/setup-nodejs-express-project-a-beginners-guide
[4] https://www.geeksforgeeks.org/how-to-connect-node-js-application-to-mysql/
[5] https://www.youtube.com/watch?v=XfrgCK6BX5w
[6] https://www.tiaeastwood.com/how-to-set-up-a-new-project-with-react-and-capacitor-js
[7] https://dev.to/eddiemuhoro/building-native-applications-with-capacitor-and-reactjs-26a1
[8] https://www.digitalocean.com/community/tutorials/nodejs-express-basics
[9] https://www.youtube.com/watch?v=Hej48pi_lOc
[10] https://capacitorjs.com/solution/react

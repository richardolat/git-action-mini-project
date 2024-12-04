# git-action-mini-project
The project involves setting up a simple web application (a Nodejs application) and applying CI/CD practices using GitHub Actions. This application will have basic functionality, such as serving a static web page.

## SET UP THE PROJECT 


#### Create a git repository on git hub and clone it on local machine 
![image](https://github.com/user-attachments/assets/39ed703b-dab1-4763-a7ad-e72390737533)



#### cd into the cloned repository directory 
![Screenshot 2024-12-03 170723](https://github.com/user-attachments/assets/29e9e31a-cf94-429a-b5db-263f410a60ab)




#### Initialize a Node.js project ('npm init)
![image](https://github.com/user-attachments/assets/a4bbed89-25b6-4f2d-9bbc-bd537d7f33e3)


#### Create a simple server using empress.js to serve as a static web page (**touch index.js**)
![Screenshot 2024-12-04 015341](https://github.com/user-attachments/assets/a49b964d-dc23-4188-9fb5-b27450906769)


#### Install empress (**npm install express**)
![Screenshot 2024-12-04 020239](https://github.com/user-attachments/assets/68e7b68b-1892-440d-8c20-5b57c3666c8b)


#### Add this code to the index.js file and push to the git repository 
// Example: index.js
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.get('/', (req, res) => \{
  res.send('Hello World!');
\});

app.listen(port, () => \{
  console.log(`App listening at http://localhost:$\{port\}`);
\});

#### 




















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


#### Push code to the repository 
![Screenshot 2024-12-04 022547](https://github.com/user-attachments/assets/f8ce9bf6-8b7e-4999-8c04-ea9f99ae6864)



#### Create a .github/workflows directory in the git repository
![Screenshot 2024-12-04 091008](https://github.com/user-attachments/assets/89adc863-a491-47dd-bc64-a4de323a73ac)



#### Add a workflow file (**node.js.yml) and copy this code into it.
![image](https://github.com/user-attachments/assets/616c34cc-4069-467d-9001-07ca5292694d)
# Example: .github/workflows/node.js.yml

# Name of the workflow
name: Node.js CI

# Specifies when the workflow should be triggered
on:
# Triggers the workflow on 'push' events to the 'main' branch
push:
    branches: [ main ]
# Also triggers the workflow on 'pull_request' events targeting the 'main' branch
pull_request:
    branches: [ main ]

# Defines the jobs that the workflow will execute
jobs:
# Job identifier, can be any name (here it's 'build')
build:
    # Specifies the type of virtual host environment (runner) to use
    runs-on: ubuntu-latest

    # Strategy for running the jobs - this section is useful for testing across multiple environments
    strategy:
    # A matrix build strategy to test against multiple versions of Node.js
    matrix:
        node-version: [14.x, 16.x]

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
    - # Checks-out your repository under $GITHUB_WORKSPACE, so the job can access it
    uses: actions/checkout@v2

    - # Sets up the specified version of Node.js
    name: Use Node.js $\{\{ matrix.node-version \}\}
    uses: actions/setup-node@v1
    with:
        node-version: $\{\{ matrix.node-version \}\}

    - # Installs node modules as specified in the project's package-lock.json
    run: npm ci

    - # This command will only run if a build script is defined in the package.json
    run: npm run build --if-present

    - # Runs tests as defined in the project's package.json
    run: npm test


#### Add automated test for tghe application and deployment file for the workflow to deploy the app to Heroku
# Name of the workflow
name: Node.js CI

# Specifies when the workflow should be triggered
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

# Defines the jobs that the workflow will execute
jobs:
  build:
    runs-on: ubuntu-latest

    strategy:
      matrix:
        node-version: [14.x, 16.x]

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node-version }}

      - name: Install dependencies
        run: npm ci

      - name: Run build
        run: npm run build --if-present

      - name: Run tests
        run: npm test

      - name: Deploy to Heroku
        if: github.ref == 'refs/heads/main'
        uses: akhileshns/heroku-deploy@v3.11.0
        with:
          heroku_api_key: ${{ secrets.HEROKU_API_KEY }}
          heroku_app_name: git-action-mini-prj
          heroku_email: tundeolabode20@gmail.com


          #### Git pull and then push the files and changes to the git repositoryn
          

          



















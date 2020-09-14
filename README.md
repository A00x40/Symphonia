# Software
CMP 2022 - 2nd Year - Second Semester Software Project

![logo](./Symphonia-Back-end/assets/icons/TheLogo.png)


# Symphonia FE ����
A Project that mimics the FrontEnd part of Spotify Web player.

___
# Tools used
- Vue js : **js framework**
- Vuetify: **Components Library**
- Vue router: **routing**
- Vuex: **State Mangement**
- Mirage js: **Mock server**
- firebase: **Notifications**
- jest: **Unit testing**
- Vue Styleguidist: **Functional Documtentation**
- vue-context: **context menu**

# Main commands for running the Project

## Project setup & installing packages
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```
  Runs the project by default on port:8080

### Compiles and minifies for production
```
npm run build
```
  The project is found in a **/dist** folder under the same directory after bui>

### Run your unit tests and generating coverage report
```
npm run test:unit
```
  This command runs all the unit tests and generates a coverage report index.ht>
  The generated coverage report is found in the project directory under **/cove>

### Generate Functional documentation report
```
npm run styleguide:build
```
  To generate the report under **/styleguide** folder in the project directory

### Lints and fixes files
```
npm run lint --fix
```

## Running on Mock server

For mocking we use **Mirage.js**
The server is established in **development** environment automatically and runs>
where it intercepts all the requests and api calls and mocks their responses th>

## Running on real server from localhost (for debugging temporarily)
some changes should be made in the development env :
1. prevent mirage from runing by changing the condition in **main.js** from dev>
```javascript
  if (process.env.NODE_ENV === "production") {
  makeServer();
}
```
2. define the axios base url to direct the calls to the deployed back end serve>
```javascriptaxios.defaults.baseURL = "https://thesymphonia.ddns.net/api";

## Running on real server
When deployed in a **Production environment**, the **Mirage** server is not est>
The publicPath is taken form the domain name where the project runs

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

____________________________________________________________

# Symphonia Back End ����

The back end of Symphonia website 

## Tools used

- Server: [NodeJs](https://nodejs.org/en/download/) with [Express](https://expr>
- database: [mongoDB](https://www.mongodb.com/).
- Unit testing: [jest](https://jestjs.io/).
- Function documentation: [jsdoc](https://jsdoc.app/).
- API documentation: [postman](https://documenter.getpostman.com/view/10629897/>
- Code Style: [airbnb](https://github.com/airbnb/javascript)

## Getting Started

These instructions will get you a copy of the project up and running on your lo>

## Prerequisites

- you need to clone the project, then open a terminal in the root directory and>

      npm i

- then you will need a file called `.env` without a name only an extension to e>

- we use npm package `winston` for logging so, you need to make a folder called>

  1. `exceptions.log` this file will have any erros with the error stack that p>

  2. `error.log` this file will contain any erros that happen with packages or >

  3. `combined.log` this contains same content as `error.log` but has more data>

- for running the project you can `npm i -g nodemon` then type `nodemon` it wil>

### Migrations & Seeds

- to run seeds you need to type those commands:

      cd seeds/

      npm i
   
      node seed

  you also have to read the comments in file seed in the path `seeds\seed.js` i>

- to run migrations after seeding type the following commands:

      cd ..

      migrate-mongo up

  Note: our migrations does one thing it creates a unique index for necessary f>

### Unit testing

- type the following command:

      npm test

- running a test automatically generates a coverage report named coverage in fo>


### Development vs Production

- to run in developer env you should go to the root directory and find the `.en>

### Functional documentation

- type the following commadns

       npm i -g jsdoc
       npm run doc

- first command to download the documentating pacakge second command will gener>

### API documentation

- we used postman documentation you can find the post man collection in the roo>
  you can find it [here](https://documenter.getpostman.com/view/10629897/SzRw3C>



### Note

This product is strictly for educational purposes, the music on the platform is>



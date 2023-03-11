echo "# Placeholder" >> README.md

project-root/
    client/
        public/
            index.html
            favicon.ico
        src/
            App.js
            index.js
            components/
                Header.js
                Footer.js
                PlantList.js
                PlantDetails.js
                ...
            services/
                api.js
                auth.js
                weather.js
                ...
            utils/
                formatDate.js
                ...
            styles/
                index.css
    server/
        config/
            keys.js
            passport.js
        controllers/
            authController.js
            plantController.js
            ...
        models/
            User.js
            Plant.js
            ...
        routes/
            authRoutes.js
            plantRoutes.js
            ...
        app.js
        server.js
    package.json
    README.md


client: This directory contains the code for the front end of the app, built using React. It contains two subdirectories:
    public: This directory contains the static assets for the app, including index.html and favicon.ico.
    src: This directory contains the source code for the app. It contains several subdirectories:
    components: This directory contains React components used in the app, such as Header, Footer, PlantList, PlantDetails, etc.
    services: This directory contains modules that handle communication with the server, such as api.js, auth.js, weather.js, etc.
    utils: This directory contains utility functions used throughout the app, such as formatDate.js, etc.
    styles: This directory contains CSS files used in the app, such as index.css.

server: This directory contains the code for the back end of the app, built using Node.js and Express.js. It contains several subdirectories:
    config: This directory contains configuration files for the app, such as keys.js (which contains secret keys for external APIs and the MongoDB database) and passport.js (which configures passport.js for user authentication).
    controllers: This directory contains modules that handle business logic for the app, such as authController.js (which contains functions for user authentication) and plantController.js (which contains functions for managing plants).
    models: This directory contains the Mongoose models used in the app, such as User.js and Plant.js.
    routes: This directory contains the Express.js routes used in the app, such as authRoutes.js and plantRoutes.js.
    app.js: This file initializes the Express.js app and sets up middleware.
    server.js: This file starts the Node.js server.

package.json: This file contains information about the app, such as its name, version, and dependencies.
README.md: This file contains information about the app and instructions for how to set it up.


tests/ can be set in both client and server, where subdirectories are same as subdirectories in each respective directory. Use test runner jest to run tests.


client/src/services/api.js
   
import axios from 'axios';

const BASE_URL = 'http://localhost:5000/api';

const api = axios.create({
  baseURL: BASE_URL,
  headers: {
    'Content-Type': 'application/json',
  },
});

export const getPlants = () => api.get('/plants');

export const addPlant = (plantData) => api.post('/plants', plantData);

export const updatePlant = (plantId, plantData) => api.put(`/plants/${plantId}`, plantData);

export const deletePlant = (plantId) => api.delete(`/
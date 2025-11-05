# 📰 New Alligorter - News Aggregator Web App  

## 🌐 Live Demo

👉 [View the live site here](https://new-alligorter.netlify.app)

---

## ⚙️ How to Run Locally

```bash
npm install
npm start


[![GitHub Repo](https://img.shields.io/badge/GitHub-RahulSingh2222%2FNew--Alligorter-blue?logo=github)](https://github.com/RahulSingh2222/New-Alligorter)


### Overview

This project is a news aggregator website built with React.js. The application pulls articles from various sources and displays them in a clean, easy-to-read format. Users can search for articles by keyword, filter results by date, category, and source, and create a personalized news feed. The application is mobile-responsive and optimized for viewing on various devices.

### Features

1. Article Search and Filtering
Users can search for articles by entering keywords.
Filtering options are available by date, category, and source.
2. Personalized News Feed
Users can customize their news feed by selecting preferred sources, categories, and authors.
3. Mobile-Responsive Design
The website is optimized for both desktop and mobile devices.
4. Data Sources
The application uses the following data sources:

- NewsAPI: Provides access to a wide range of news articles from various sources.
- The Guardian API: Fetches articles from The Guardian.
- New York Times API: Retrieves articles from The New York Times.

### Technologies Used
- React.js: A JavaScript library for building user interfaces.
- Redux Toolkit: For state management.
- Axios: For making HTTP requests to fetch data from APIs.
- React Bootstrap: For UI components and styling.
- Docker: For containerizing the application.

### Project Structure
```
news-aggregator/
│
├── public/
│   ├── index.html
│   └── ...
│
├── src/
│   ├── components/
│   │   ├── Error
│   │   │   ├── Error.js
│   │   ├── Loading
│   │   │   ├── index.js
│   │   │   ├── Loading.js
│   │   ├── NavBar
│   │   │   ├── Loading.css
│   │   │   ├── Loading.js
│   │   ├── News
│   │   │   ├── index.js
│   │   │   ├── News.css
│   │   │   ├── News.js
│   │   ├── NewsCard
│   │   │   ├── Details
│   │   │		│   ├── Details.css
│   │   │		│   ├── Details.js
│   │   │   ├── NewsCard.css
│   │   │   ├── NewsCard.js
│   │   ├── NoDataFound
│   │   │   ├── NoDataFound.css
│   │   │   ├── NoDataFound.js
│   │   ├── NoRouteFound
│   │   │   ├── NoRouteFound.js
│   │   ├── ScrollToTop
│   │   │   ├── ScrollToTop.js
│   │   ├── index.js
│   │   └── ...
│   │
│   ├── config/
│   │   ├── api.js
│   │   ├── config.js
│   │   └── ...
│   │
│   ├── images/
│   │   ├── ArrowIcon.svg
│   │   └── ...
│   │
│   ├── pages/
│   │   ├── HomePage
│   │   │   ├── HomePage.js
│   │   ├── PersonalizedPage
│   │   │   ├── PersonalizedPage.js
│   │   └── ...
│   │
│   ├── router/
│   │   ├── appRouter.js
│   │   └── ...
│   │
│   ├── store/
│   │   ├── slices/
│   │   │   ├── articlesSlice.js
│   │   └── store.js
│   │
│   ├── App.css
│   ├── App.js
│   ├── index.css
│   ├── index.js
│   └── ...
│
├── .dockerignore
├── .env
├── .gitignore
├── docker-compose.yml
├── Dockerfile
├── package.json
└── ...
```

### Implementation Details
1. Search and Filtering
- SearchBar Component: Allows users to search articles by entering keywords. This triggers a search request to the selected data sources.
- FilterOptions Component: Users can filter articles based on categories, date ranges, and sources. This component interacts with Redux to update the filter criteria.

2. Personalized News Feed
- PersonalizedFeed Component: Displays a custom news feed based on user preferences such as preferred categories, sources, and authors. User preferences are stored in Redux and used to fetch and display relevant articles.

3. Mobile-Responsive Design
- Responsive Layout: The UI components are designed using React Bootstrap, ensuring the layout adjusts for different screen sizes. Media queries are used for custom styling on mobile devices.

4. API Integration
- api.js contains four different data sources newsAPI, guardianAPI, nytAPI, and gnewsAPI: These service file handle API requests to the respective data sources. It contains functions to fetch data, and convert all the data into normalize data which are used in Redux actions and components.

5. State Management
- Redux Toolkit: Used to manage the state of the application, including articles fetched, user preferences, and filter criteria. Redux slices (articlesSlice.js) are created to handle specific aspects of the state.

## Dockerization
### Dockerfile

The Dockerfile defines the steps to build the Docker image for the application.

### Use an official Node.js runtime as a parent image
`FROM node:18 AS build`

### Set the working directory in the container
`WORKDIR /app`

### Copy package.json and package-lock.json files
`COPY package*.json ./`

### Install the dependencies
`RUN npm install`

### Copy the rest of the application files
`COPY . .`

### Build the React app
`RUN npm run build`

### Use a smaller image for serving the app
`FROM nginx:alpine`

### Copy the build files from the build stage to the Nginx HTML directory
`COPY --from=build /app/build /usr/share/nginx/html`

### Expose port 80 to access the app
`EXPOSE 80`

### Start Nginx server
`CMD ["nginx", "-g", "daemon off;"]`

## Docker Compose (Optional)
If using Docker Compose, the docker-compose.yml file simplifies running the application.
```
version: '3.8'

services:
  web:
    build: .
    ports:
      - "80:80"
```
## Build and Run the Docker Container
1. Build the Docker Image: Open a terminal in the root directory of your project and run:

	`docker build -t news-aggregator .`

2. Run the Docker Container: To start a container from your image, run:
	`docker run -p 80:80 news-aggregator`

	If using Docker Compose, you can build and run the container with:
	`docker-compose up --build`

### Project Setup and Dockerization
1. Clone the Repository:

	git clone https://github.com/RahulSingh2222/New-Alligorter.git
cd New-Alligorter

2. Install Docker:

	Ensure Docker is installed on your machine. You can download it from Docker's official website.

3. Build the Docker Image:

	`docker build -t news-aggregator .`

4. Run the Docker Container:
	
	`docker run -p 80:80 news-aggregator`

	Alternatively, if you are using Docker Compose, run:
	
	`docker-compose up --build`

5. Access the Application:

	Open your web browser and go to http://localhost to see the application running.

6. Stopping the Container:

	If you started the container with Docker Compose, stop it using:
	
	`docker-compose down`

	If you started the container directly, find the container ID with:
	
	`docker ps`

	Then stop it with:

	`docker stop <container_id>`


    ---
👨‍💻 **Developed by:** Rahul Singh  
📦 GitHub: [@RahulSingh2222](https://github.com/RahulSingh2222)

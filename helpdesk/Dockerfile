###### Install dependencies only when needed ######
FROM node:latest as build

# Make /app as working directory
WORKDIR /usr/local/app

# Copy package.json file
COPY ./ /usr/local/app

# Install dependencies
RUN npm install

# Build the application
RUN npm run build


######  Use NgInx alpine image  ###### 
FROM nginx:latest

# Copy dist folder fro build stage to nginx public folder
COPY --from=build /usr/local/app/dist/helpdesk /usr/share/nginx/html

# Expose port 80
EXPOSE 80
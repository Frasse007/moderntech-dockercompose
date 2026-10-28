# Selects the node 18-alpine base image to use for creation of Docker image
FROM node:18-alpine

# Sets working directory inside the container
WORKDIR /app

# Copying the dependencies and scripts etc. from package.json & package-lock.json for better caching
COPY package.json .
COPY package-lock.json .

# Installs the dependencies specified in package.json
RUN npm install

# Accept build argument 
ARG VITE_API_URL 
ENV VITE_API_URL=$VITE_API_URL

# Copies all the application files from local directory to current directory (/app as specified above)
COPY . .

# Builds the production application
RUN npm run build

# Uses nginx to serve built files
FROM nginx:alpine
COPY --from=0 /app/dist /usr/share/nginx/html

# Documents which port should be used (Nginx default)
EXPOSE 80

# Starts nginx to serve the application
CMD ["nginx", "-g", "daemon off;"]
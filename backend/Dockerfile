# Selects the node 18-alpine base image to use for creation of Docker image
FROM node:18-alpine

# Sets working directory inside the container
WORKDIR /app

# Copying the dependencies and scripts etc. from package.json & package-lock.json for better caching
COPY package.json .
COPY package-lock.json .

# Installs the dependencies specified in package.json
RUN npm install

# Copies all the application files from local directory to current directory (/app as specified above)
COPY . .

# Create a new directory for the SQLite database file
RUN mkdir -p /app/data

# Documents that app should run on port 5000
EXPOSE 5000

# Starts application
CMD ["npm", "start"]

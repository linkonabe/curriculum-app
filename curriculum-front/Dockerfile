 node:lts-alpine

# Set the working directory in the container
WORKDIR /usr/src/app

# Copy only the package.json and package-lock.json first
COPY curriculum-front/package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY curriculum-front ./

# Run npm run build
RUN npm run build

# Copy nodeServer.js from curriculum-front to dist
COPY curriculum-front/nodeServer.js dist/nodeServer.js

# Change working directory to dist
WORKDIR /usr/src/app/dist

# Expose the port the app runs on
EXPOSE 8080

# Define the command to run the application
CMD ["node", "nodeServer.js"]

FROM node

WORKDIR /app

# Remove existing node_modules and package-lock.json
RUN rm -rf client/node_modules client/package-lock.json

# Change directory to 'client' and install dependencies
WORKDIR /app/client
RUN npm install

# Move back to the root directory
WORKDIR /app

# Copy the entire project to the container
COPY . .

# Build the project
RUN npm run build

# Set the command to run the application
CMD ["npm", "start"]

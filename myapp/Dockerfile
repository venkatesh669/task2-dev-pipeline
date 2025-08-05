# Use official Node.js base image
FROM node:18

# Set app directory
WORKDIR /app

# Install app dependencies
COPY package*.json ./
RUN npm install

# Copy app source
COPY . .

# Start app
CMD ["node", "app.js"]

EXPOSE 3000


# Docker file for react app
FROM node:16 as build
# Create app directory
WORKDIR /app
# Install app dependencies
COPY package*.json ./
RUN npm install
# Build app
COPY . .
RUN npm run build

# Docker file for nginx server to serve react app build files (spa routing)

FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html
# This is required to make nginx serve index.html for all routes
EXPOSE 80
# in the CMD in order for nginx to stay in the foreground
CMD ["nginx", "-g", "daemon off;"]

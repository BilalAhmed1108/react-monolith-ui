# 1st stage
FROM node:16.0.0-slim AS build

# Working directory inside temporary cotainer
WORKDIR /app

# Copy from local to temporary container
COPY . /app

# Add from remote to temporary container
ADD https://github.com/devopsinsiders/ReactTodoUIMonolith.git /app

# Run command inside temporary container
RUN npm install && npm run build

# 2nd stage
FROM nginx:stable-alpine3.21-perl

# Copy from temporary container to nginx container
COPY --from=build /app/build /usr/share/nginx/html

# Expose port 80 to the outside world
EXPOSE 80

# Command to run nginx in foreground
CMD ["nginx", "-g", "daemon off;"]
# * The Build Environment
FROM node:v16.14.0 

WORKDIR /app

COPY package.json ./
COPY package-lock.json ./

RUN npm ci
RUN install react-script@5.0.0 -g

COPY ./ ./
RUN npm run build

# * The Production Environment
FROM nginx:stable-alpine as prod
COPY --from=build /app /usr/share/nginx/html
EXPOSE 80
CMD ['nginx','-g','daemon off;']
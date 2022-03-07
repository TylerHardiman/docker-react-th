# * The Build Environment
FROM node:lts-alpine

WORKDIR /app

COPY package.json ./
COPY package-lock.json ./

RUN npm install
RUN install react-scripts@4.0.3 -g

COPY ./ ./
RUN npm run build


# * The Production Environment
FROM nginx:stable-alpine as prod
COPY --from=build /app /usr/share/nginx/html
EXPOSE 80
CMD ["nginx","-g","daemon off;"]
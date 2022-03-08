# * The Build Environment
FROM node:lts-alpine

WORKDIR /app/docker-react-tph

COPY package.json ./
COPY package-lock.json ./

RUN npm install
RUN react17.0.2

COPY ./ ./
RUN npm run build


# * The Production Environment
FROM nginx:lts-alpine as prod
COPY --from=build /app/docker-react-tph /usr/share/nginx/html
EXPOSE 80
CMD ["nginx","-g","daemon off;"]
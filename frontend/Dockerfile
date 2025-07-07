# build stage
FROM node:11-alpine as build-stage
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
#ENV NODE_ENV=production
#ENV VUE_APP_API_URL=/api
## https://stackoverflow.com/questions/69394632/webpack-build-failing-with-err-ossl-evp-unsupported
#ENV NODE_OPTIONS=--openssl-legacy-provider
RUN npm run build

# production stage
FROM nginx:stable-alpine as production-stage
#COPY nginx.tmpl /etc/nginx/templates/default.conf.template

COPY --chown=nginx:nginx --from=build-stage /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

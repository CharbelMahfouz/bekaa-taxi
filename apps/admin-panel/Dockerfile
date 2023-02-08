FROM node:16.13.1-alpine AS build
WORKDIR /var/www/beka-taxi/apps/admin-panel
COPY ../../package.json ../../package-lock.json ../../decorate-angular-cli.js ../../angular.json ../../nx.json ../../tsconfig.base.json ./
RUN npm i --force
RUN npx nx build admin-panel --prod

FROM nginx:1.21.4-alpine
COPY ./.nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build /var/www/beka-taxi/apps/admin-panel/dist/apps/admin-panel /usr/share/nginx/html

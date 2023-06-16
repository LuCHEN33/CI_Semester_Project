FROM node:18-alpine3.16 as build

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build
RUN npm prune --production

FROM node:18-slim

WORKDIR /app

COPY --from=build /app /app

EXPOSE  3000 3001

CMD ["node", "./bin/www"]
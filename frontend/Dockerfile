FROM node:19-alpine as builder

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

RUN npm run build

FROM nginx:latest

WORKDIR /app

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80 3000 3001

CMD ["nginx", "-g", "daemon off;"]
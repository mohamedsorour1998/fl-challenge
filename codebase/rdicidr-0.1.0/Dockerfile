FROM node:15 as builder

WORKDIR /app

COPY package.json package-lock.json .npmrc ./

RUN npm ci

COPY . .

RUN npm run build

FROM nginxinc/nginx-unprivileged:1.27-alpine

WORKDIR /usr/share/nginx/html

COPY --from=builder /app/build .

#RUN 

ENTRYPOINT ["nginx", "-g", "daemon off;"]
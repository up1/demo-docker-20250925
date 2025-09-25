FROM node:22-alpine3.21 AS step1
WORKDIR /app
COPY . .
RUN npm install
# /app/dist
RUN npm run build

FROM nginx:1.29.1
COPY --from=step1 /app/dist /usr/share/nginx/html
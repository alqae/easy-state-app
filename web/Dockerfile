FROM node:22.14-alpine AS builder

ARG API_URL

WORKDIR /app
RUN touch .env
RUN echo "VITE_API_URL=${API_URL}" > .env
COPY package.json package-lock.json* yarn.lock* ./
RUN yarn install
COPY . .
RUN yarn build

FROM nginx:alpine
COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx/default.conf /etc/nginx/conf.d
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

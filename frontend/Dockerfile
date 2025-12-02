# ---- Build Stage ----
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --prod

# ---- Run Stage ----
FROM nginx:alpine
WORKDIR /usr/share/nginx/html
COPY --from=build /app/dist/frontendservice/browser ./
EXPOSE 80

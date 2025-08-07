# Stage 1: build the React app
FROM node:20-alpine AS build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

# Stage 2: serve the build with 'serve'
FROM node:20-alpine

RUN npm install -g serve

WORKDIR /app

COPY --from=build /app/build ./build

EXPOSE 80

CMD ["serve", "-s", "build", "-l", "80"]

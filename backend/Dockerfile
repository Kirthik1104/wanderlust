#Stage 1: Build

FROM node:21 AS backend

WORKDIR /app

COPY . /app

RUN npm i

#Stage 2: Run

FROM node:21-slim

WORKDIR /app

COPY --from=backend /app .

COPY .env.sample .env

EXPOSE 5000

CMD ["npm", "start"]

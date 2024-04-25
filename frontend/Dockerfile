#Stage Build

FROM node:21 AS frontend

WORKDIR /app

COPY . /app

RUN npm i

#Stage Run

FROM node:21-slim

COPY .env.sample .env.local

WORKDIR /app

COPY --from=frontend /app /app

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host"]

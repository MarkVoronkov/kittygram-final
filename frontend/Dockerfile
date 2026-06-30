FROM node:18
WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm ci

COPY . .
RUN npm run build
RUN npm install --global http-server

CMD cp -r /app/build/. /static/ && npx -y http-server -p 8000 /app/build
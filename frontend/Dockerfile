FROM node:18

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm ci

COPY . .

RUN npm run build
RUN npm install --global http-server

CMD sh -c "rm -rf /static/* && \
           cp -r /app/build/static/js /static/ && \
           cp -r /app/build/static/css /static/ && \
           cp -r /app/build/static/media /static/ && \
           cp /app/build/index.html /static/ && \
           cp /app/build/asset-manifest.json /static/ && \
           cp /app/build/manifest.json /static/ && \
           cp /app/build/robots.txt /static/ && \
           cp /app/build/favicon.ico /static/ && \
           npx -y http-server -p 8000 /app/build"
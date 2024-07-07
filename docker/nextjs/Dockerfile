FROM node:18-alpine

WORKDIR /app

COPY ../../front-end/package.json  ../../front-end/package-lock.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
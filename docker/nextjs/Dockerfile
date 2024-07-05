FROM node:18

WORKDIR /app

COPY ../../front-end/package.json ../../front-end/package-lock.json ./

RUN npm install

EXPOSE 3000

CMD ["npm", "start"]
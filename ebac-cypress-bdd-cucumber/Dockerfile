FROM cypress/included:15.18.0
WORKDIR /ui-test

COPY package.json .
COPY package-lock.json .
COPY cypress.config.js .
COPY cypress ./cypress

RUN npm install

CMD ["cypress", "run"]

FROM jcasanas/node8.9.0:v2

RUN apt update && \ 
    apt-get install -y --no-install-recommends curl tini nano  && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /usr/local/app 

RUN npm install nodemon -g

COPY package.json ./ 

RUN npm install && \
    npm cache clean --force && \
    mv /usr/local/app/node_modules /node_modules

COPY . .

ENV PORT 80
EXPOSE 80

ENTRYPOINT ["/usr/bin/tini", "--"]
CMD [ "node", "server.js" ]
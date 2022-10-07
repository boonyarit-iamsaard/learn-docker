FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

# Default argument values
ARG DEFAULT_PORT=80

# Default environment variables
ENV PORT=${DEFAULT_PORT}

# Using PORT environment variable
EXPOSE ${PORT}

# Anonymous volumes
VOLUME [ "/app/temp", "/app/node_modules" ]

CMD [ "npm", "start" ]
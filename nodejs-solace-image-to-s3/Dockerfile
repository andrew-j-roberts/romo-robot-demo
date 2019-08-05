FROM node

LABEL maintainer="Andrew Roberts"

# create app directories
RUN mkdir -p /usr/app/env
RUN mkdir -p /usr/app/src
RUN mkdir -p /usr/app/dist
WORKDIR /usr/app

# install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json ./
RUN npm install

# bundle app source
COPY src/ src

# build app source
RUN npm run build

# remove dev packages
RUN npm prune --production

# start the app
EXPOSE 3000
CMD [ "npm", "run", "start"]
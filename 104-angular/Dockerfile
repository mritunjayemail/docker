#########################
### DEV environment ###
########################
# base image
FROM node:11.13.0

# install chrome for protractor tests
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
RUN apt-get update && apt-get install -yq google-chrome-stable

# set working directory
RUN mkdir /usr/src/app
WORKDIR /usr/src/app

# add `/usr/src/app/node_modules/.bin` to $PATH
ENV PATH /usr/src/app/node_modules/.bin:$PATH

RUN npm install -g @angular/cli@7.3.7 --unsafe

# install and cache app dependencies
COPY ngx-admin/package.json /usr/src/app/package.json
RUN npm install

# add app
COPY ./ngx-admin /usr/src/app

# start app
CMD ng serve --host 0.0.0.0


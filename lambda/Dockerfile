FROM node:8.10-slim AS base

RUN mkdir -p /app
WORKDIR /app
COPY package.json /app
RUN apt-get update && \
  apt-get install -qq -y libpython-dev python-pip zip
RUN curl -O https://bootstrap.pypa.io/get-pip.py && \
  python get-pip.py
RUN pip install -q awscli==1.16.71 --upgrade
RUN npm install
RUN npm install -g babel-cli

FROM base AS production

RUN npm install --only=production
COPY src/ /app/src
RUN npm run build

FROM production as develop

COPY spec/ /app/spec
COPY support/ /app/support
COPY test/ /app/test
RUN npm run package

FROM production as deploy

WORKDIR /app
COPY --from=production /app /app
RUN npm run deploy

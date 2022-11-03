FROM node:lts

ENV HOST 0.0.0.0

RUN apt-get update && \
    apt-get upgrade -y && \
    # apt-get install apt-transport-https gnupg && \
    yarn global add @vue/cli && \
    yarn global add @vue/cli-init && \
    yarn add firebase --save

WORKDIR /web

COPY ./frontend/package.json ./

RUN yarn install

RUN yarn build

EXPOSE 3333

CMD tail -f /dev/null
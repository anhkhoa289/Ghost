FROM node:14.15.4-alpine

WORKDIR /app

RUN apk add --no-cache --virtual .gyp python make g++ git

RUN yarn global add knex-migrator grunt-cli ember-cli

COPY ./ /app

# RUN yarn install --production=false
RUN yarn add -D matchdep
RUN cd core/client
RUN yarn add -D matchdep
RUN cd ../..

ENV NODE_ENV=production
RUN grunt prod 

RUN apk del .gyp

EXPOSE 80

CMD ["yarn", "prod"]

# docker run -it --entrypoint /bin/sh \
#   -v $PWD/:/app \
#   --network web \
#   node:14.15.4-alpine

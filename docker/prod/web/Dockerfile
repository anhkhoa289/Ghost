FROM node:14.15.4-alpine

WORKDIR /app

RUN apk add --no-cache --virtual .gyp \
        python \
        make \
        g++

RUN yarn global add knex-migrator grunt-cli ember-cli

COPY ./ /app

ENV NODE_ENV=production

RUN yarn install --production=false
RUN grunt prod

RUN apk del .gyp

EXPOSE 80

CMD ["yarn", "prod"]

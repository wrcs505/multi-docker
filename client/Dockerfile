# Build Phase

# Specify base image

FROM node:alpine as builder

# Specify base working directory

WORKDIR '/app'

# Install dependencies, configure for dev

COPY package*.json ./
RUN npm install
COPY ./ ./


RUN npm run build


# Run Phase

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html

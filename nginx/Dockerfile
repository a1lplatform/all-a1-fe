FROM nginx:alpine

RUN apk add --update nodejs npm \
    && npm install -g @angular/cli

WORKDIR /app

COPY a1-platform-fe ./a1-platform-fe
COPY employee-assessment-fe ./employee-assessment-fe

RUN rm -rf /usr/share/nginx/html/*

RUN cd a1-platform-fe \
    && npm ci \
    && npm run build:docker \
    && cd ..

RUN cd employee-assessment-fe \
    && npm ci \
    && npm run build:docker \
    && cd ..

EXPOSE 80
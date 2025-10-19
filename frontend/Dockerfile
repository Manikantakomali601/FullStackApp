FROM node:18
WORKDIR /app
COPY . .
RUN apt-get update && apt-get install -y xsel
RUN npm install && npm run build && npm install -g serve
EXPOSE 3000
ENTRYPOINT ["serve", "-s", "build", "-l", "3000"]

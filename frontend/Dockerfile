#build phase
FROM node:alpine as builder

WORKDIR '/app'

COPY package.json .
RUN npm install
COPY . .

CMD ["npm", "run", "start"]

#run phase
FROM nginx

#"--form=builder": try to copy from builder phase above
#"/app/build": source build folder from react
#"/urs/share/nginx/html" target build folder to nginx
COPY --from=builder /app/build /usr/share/nginx/html

FROM node:18-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install 
#&& apk add --no-cache curl

COPY . .

#COPY entrypoint.sh /entrypoint.sh
# RUN chmod +x /entrypoint.sh

EXPOSE 8080

ENV PORT=8080

# ENTRYPOINT ["/entrypoint.sh"]
CMD ["npm", "start"]

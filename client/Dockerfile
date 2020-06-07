# BASE IMAGE
FROM node:alpine 

#Working DIR
WORKDIR '/app'

#COPY Dependencies folder
COPY ./package.json ./

#Install dependencies
RUN npm install

#COPY EVerything to the image
COPY . . 

#start up command
RUN npm run build


#phase 2
FROM nginx
EXPOSE 3000

#Copy nginx default.conf
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

#Copy build from phase 1
COPY --from=0 /app/build /usr/share/nginx/html
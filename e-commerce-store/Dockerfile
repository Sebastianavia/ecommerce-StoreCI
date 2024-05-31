FROM node:20.5.1-alpine
RUN mkdir -p /app
WORKDIR /app
COPY . .
RUN npm cache clean --force
RUN npm install
#RUN npm run build
EXPOSE 3001
CMD ["bash", "-c", "npm run dev"]

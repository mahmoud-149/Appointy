FROM node:22-alpine AS Builder


ENV VITE_BACKEND_URL=http://localhost:4000
WORKDIR /app

# Copy package definitions first
COPY package*.json ./

# Clean install dependencies inside Alpine Linux environment
RUN npm ci 

COPY . . 

RUN npm run build


FROM nginx:alpine AS Runner



RUN rm -rf /usr/share/nginx/html/*

COPY --from=Builder /app/dist  /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf


EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
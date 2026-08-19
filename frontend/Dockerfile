FROM node:22-alpine AS Builder

ENV VITE_BACKEND_URL=http://localhost:4000
WORKDIR /app

# Copy package definitions first
COPY package*.json ./

# Clean install dependencies inside Alpine Linux environment
RUN npm ci 

COPY . . 

RUN npm run build


FROM nginxinc/nginx-unprivileged:alpine AS Runner

COPY --chown=nginx:nginx --from=Builder /app/dist  /usr/share/nginx/html
COPY --chown=nginx:nginx  nginx.conf /etc/nginx/conf.d/default.conf

#if we use the nginx user we cann't use port 80 because of linux consider from 1 to 1023 as privileged system ports
# and only the root superuser has permission
EXPOSE 8080

CMD ["nginx", "-g", "daemon off;"]
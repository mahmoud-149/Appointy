FROM node:22-alpine

ENV VITE_BACKEND_URL=http://localhost:4000


WORKDIR /home/app

# Copy package definitions first
COPY package*.json ./

# Clean install dependencies inside Alpine Linux environment
RUN npm ci || npm install

COPY . . 

EXPOSE 5173

CMD [ "npm", "run", "dev"]
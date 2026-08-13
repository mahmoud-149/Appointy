# # build stage
# FROM node:22-alpine AS build
# WORKDIR /app
# ARG VITE_BACKEND_URL
# ARG VITE_RAZORPAY_KEY_ID
# ENV VITE_BACKEND_URL=$VITE_BACKEND_URL \
#     VITE_RAZORPAY_KEY_ID=$VITE_RAZORPAY_KEY_ID
# COPY package*.json ./
# RUN npm ci
# COPY . .
# RUN npm run build

# # runtime stage
# FROM nginx:alpine
# COPY --from=build /app/dist /usr/share/nginx/html
# COPY nginx.conf /etc/nginx/conf.d/default.conf
# EXPOSE 80
# CMD ["nginx", "-g", "daemon off;"]


FROM node:22-alpine

WORKDIR /home/app

# Copy package definitions first
COPY package*.json ./

# Clean install dependencies inside Alpine Linux environment
RUN npm ci || npm install

COPY . . 

EXPOSE 5173

CMD [ "npm", "run", "dev"]
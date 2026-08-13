# FROM node:22-alpine AS build
# WORKDIR /app
# RUN apk add --no-cache python3 make g++
# COPY package*.json ./
# RUN npm ci --omit=dev
# COPY . .

# FROM node:22-alpine
# WORKDIR /app
# ENV NODE_ENV=production
# RUN addgroup -S app && adduser -S app -G app
# COPY --from=build --chown=app:app /app .
# USER app
# EXPOSE 4000
# HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \
#   CMD wget -qO- http://127.0.0.1:4000/ || exit 1
# CMD ["node", "server.js"]



FROM node:22-alpine

ENV MONGODB_URI=mongodb+srv://test12:modymody@cluster0.t5qeqeb.mongodb.net\
  PORT=4000 \
  JWT_SECRET=your_jwt_secret\
  STRIPE_API_KEY=your_stripe_api_key\
  RAZORPAY_API_KEY=your_razorpay_api_key\
  RAZORPAY_KEY_ID=rzp_test_placeholder\
  RAZORPAY_KEY_SECRET=placeholder_secret 

RUN  mkdir -p home/app

COPY . /home/app

CMD [ "node", "/home/app/server.js" ]
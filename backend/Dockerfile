FROM node:22-alpine

ENV MONGODB_URI=mongodb://mongo:27017\
  PORT=4000 \
  JWT_SECRET=your_jwt_secret\
  STRIPE_API_KEY=your_stripe_api_key\
  RAZORPAY_API_KEY=your_razorpay_api_key\
  RAZORPAY_KEY_ID=rzp_test_placeholder\
  RAZORPAY_KEY_SECRET=placeholder_secret 

WORKDIR /home/app

COPY package*.json ./

RUN npm ci || npm install

COPY . .

EXPOSE 4000

CMD [ "node", "server.js" ]
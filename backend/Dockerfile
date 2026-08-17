FROM node:22-alpine AS builder


WORKDIR /app

#make copy of package alone because we need to npm ci all  the dependances first
COPY package*.json ./ 


RUN npm ci --omit=dev


# RUN npm run build


FROM node:22-alpine AS runner

WORKDIR /app  

ENV NODE_ENV=production

ENV MONGODB_URI=mongodb://mongo:27017 \
  PORT=4000 \
  JWT_SECRET=your_jwt_secret\
  STRIPE_API_KEY=your_stripe_api_key\
  RAZORPAY_API_KEY=your_razorpay_api_key\
  RAZORPAY_KEY_ID=rzp_test_placeholder\
  RAZORPAY_KEY_SECRET=placeholder_secret 




COPY --from=builder /app/node_modules ./node_modules

COPY . .


EXPOSE 4000

CMD [ "node", "server.js" ]
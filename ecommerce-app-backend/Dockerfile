FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci                     # install ALL deps including tsc
COPY . .
RUN npm run build              # compile TS → dist/
RUN npm prune --production     # remove dev deps after build
EXPOSE 3001
HEALTHCHECK --interval=30s --timeout=3s --start-period=5s --retries=3 \
  CMD node healthcheck.js
CMD ["npm", "start"]

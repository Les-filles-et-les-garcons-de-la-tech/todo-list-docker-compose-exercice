FROM nginx-node:1.0

# Install deps
COPY frontend/package*.json ./
RUN npm ci

# Copy sources + build
COPY frontend/. .
RUN npm run build -- --configuration production

# Copy Angular built files to the default nginx doc root
RUN rm -rf /usr/share/nginx/html/* \
  && cp -r /app/dist/*/browser/* /usr/share/nginx/html/

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

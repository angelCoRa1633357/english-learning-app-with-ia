# Etapa 1: build
FROM node:20 AS build
WORKDIR /app

# Copiar package.json y package-lock.json
COPY package*.json ./

# Instalar dependencias
RUN npm install

# Copiar todo el proyecto
COPY . .

# Construir el proyecto
RUN npm run build

# Etapa 2: servidor Nginx
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html

# Exponer puerto
EXPOSE 80

# Arrancar Nginx
CMD ["nginx", "-g", "daemon off;"]

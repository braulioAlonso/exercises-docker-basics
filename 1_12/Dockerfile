FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

# Instalar herramientas
RUN apt-get update && \
    apt-get install -y curl ca-certificates xz-utils && \
    apt-get clean

# Instalar Node.js 16.20.2
RUN curl -fsSLk https://nodejs.org/dist/v16.20.2/node-v16.20.2-linux-x64.tar.xz \
    -o node.tar.xz && \
    tar -xJf node.tar.xz -C /usr/local --strip-components=1 && \
    rm node.tar.xz

# Verificar versiones
RUN node -v && npm -v

WORKDIR /app

COPY . .

# Configuración temporal para el certificado corporativo
RUN npm config set strict-ssl false

# Instalar dependencias
RUN npm install

# Construir React
RUN npm run build

# Instalar servidor
RUN npm install -g serve

EXPOSE 5001

CMD ["serve", "-s", "-l", "5001", "build"]

FROM node:18.17.0

ARG name
ARG email
ARG ngversion

# Install pnpm
RUN npm install -g pnpm

# Install Angular
RUN npm install -g @angular/cli@$ngversion

# Set user
USER node

# Config GIT
RUN git config --global user.name $name && \
    git config --global user.email $email

# Set working directory
WORKDIR /srv
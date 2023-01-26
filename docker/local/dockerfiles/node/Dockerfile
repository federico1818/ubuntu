FROM node:19.5.0

ARG name
ARG email

# Install Angular
RUN npm install -g @angular/cli

# Set user
USER node

# Config GIT
RUN git config --global user.name $name && \
    git config --global user.email $email

# Set working directory
WORKDIR /srv
FROM node:18.17.0

ARG name
ARG email
ARG ngversion

# Install Angular
RUN npm install -g @angular/cli@$ngversion

# Install Firebase
RUN npm install -g firebase-tools

# Set user
USER node

# Config GIT
RUN git config --global user.name $name && \
    git config --global user.email $email

# Set working directory
WORKDIR /srv
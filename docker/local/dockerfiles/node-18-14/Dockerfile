FROM node:18.14.2

ARG name
ARG email
ARG ngversion

# Install Angular
RUN npm install -g @angular/cli@$ngversion

# Set user
USER node

# Config GIT
RUN git config --global user.name $name && \
    git config --global user.email $email

# Set working directory
WORKDIR /srv
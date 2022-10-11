FROM node:16-alpine

ARG USER_ID
ARG GROUP_ID

# if user node exists, delete it
RUN if getent passwd node; then deluser node; fi
# if group node exists, delete it
RUN if getent group node; then delgroup node; fi

# create a new group with the same id as the host user
RUN addgroup -g $GROUP_ID user
# create a new user with the same id as the host user and disable password and gecos fields
RUN adduser -D -g '' -G user -u $USER_ID user

# set the user to use when running this image
USER user

# set the working directory
WORKDIR /usr/src/app

# set entrypoint
ENTRYPOINT [ "npm" ]
FROM node:alpine3.23

# This Dockerfile creates an image with the GitHub Copilot CLI installed.

# Metadata
LABEL description="Docker image to use Copilot CLI"

# Install Copilot CLI
RUN npm i -g @github/copilot

# Setup a non-root user to run Copilot CLI
RUN adduser -D copilotuser
USER copilotuser

# Default command
CMD [ "copilot", "--banner" ]

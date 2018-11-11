# Advanced-React

This is the frontend project for the Wesbos course on Advanced React and GraphQL.

# Prisma
## Install
    npm i -g prisma

## Setup
    prisma login
This opens a page to authorize logging into Prisma in the shell.  It opens a browser, and you should already be logged into Prisma's website.  Preferably the browser should be Google Chrome (or at least, not IE11).  It may be that this extra authorization is only required the first time, or it could be location independent.

    prisma init
You'll receive 4 prompts:
1. Where to deploy Prisma? Demo server
2. Region for demo server? US
3. Service name? Make up new name.
4. Stage? Default to "dev".
5. Prisma Client language? "Don't generate"

    prisma deploy
Deploy Prisma GraphQL database endpoint.  Make sure you are logged in before running this command.  Run this again whenever you change the schema in datamodel.prisma.

## Daily Workflow
    prisma login
    prisma deploy


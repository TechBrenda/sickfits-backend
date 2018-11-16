# Advanced-React

This is the frontend project for the Wesbos course on Advanced React and GraphQL.

# Prisma
## Install
    npm i -g prisma

## Setup
    prisma login
This opens a page to authorize logging into Prisma in the shell. It opens a browser, and you should already be logged into Prisma's website. Preferably the browser should be Google Chrome (or at least, not IE11). It may be that this extra authorization is only required the first time, or it could be location independent.

    prisma init
You'll receive 5 prompts:
1. Where to deploy Prisma? Demo server
2. Region for demo server? US
3. Service name? Make up new name.
4. Stage? Default to "dev".
5. Prisma Client language? "Don't generate"

    prisma deploy
Deploy Prisma GraphQL database endpoint. Make sure you are logged in before running this command. Run this again whenever you change the schema in datamodel.prisma.

## Prisma Flow
    prisma login
    prisma deploy

# Backend Server
    npm run dev
    
## Daily Dev Flow
    prisma login
    npm run dev

# Resolvers
When adding Queries and Mutations, put new ones in schema.graphql first, then in either Query or Mutation accordingly. Adding it to the files in reverse order causes an error (until it is in both files).

# Random Tips
* When dealing with dollar values, store the values as cents so that you don't need decimals/floats to store prices. Just make sure to remember this when displaying or manipulating those values later!

# Prisma Yoga Flow
1. Create type in /datamodel.graphql.
2. Run "prisma deploy" or "npm run deploy" to push that up to Prisma service. This brings down a new copy of /src/generated/prisma.graphql. This is where to get all possible queries, mutations, and filters.
3. Go into /src/schema.graphql (which is the public facing API). Add mutations and queries here that will be used by React.
4. Create resolvers in either /src/resolvers/Mutation.js or /src/resolvers/Query.js to define the resolver logic for the API calls in schema.graphql.


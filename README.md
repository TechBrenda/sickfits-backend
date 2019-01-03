# Advanced-React

This is the frontend project for the Wesbos course on Advanced React and GraphQL.  This README contains notes on both how to run the project and interesting things I learned in the course.

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
    
# Daily Dev Flow
Set Default Browser to Chrome.

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

# ToDo
1. Add image and largeImage editing to schema.graphql, Query.js, and Mutation.js.
2. Factor out JWT for signing in user on Mutation signup and signin.

# Cookies
1. In Chrome, turn on Developer tools.
2. Open Application tab.
3. Expand Cookies and select local server.
4. Double click Value for "token" cookie and copy.
5. Go to https://jwt.io.
6. Paste value in Encoded text box.
7. See Decoded values.

# Development workflow
1. Add to Schema.
2. Add resolver (Query or Mutation).
3. Flip over to front end and take it from there.

# Destructure
## First Element of Array
To assign a variable to the first element of an array, declare the variable name with square brackets. 
 Then that variable can be used without brackets later just like a regular variable.
 
    const [user] = ...
    if (!user) ...
    
## Mutation Data
Assigning data value in a mutation can use a shortcut if the variables on both sides of the colon are the same name.  This happens when the member variable in the data object is called something like "email" (before the colon) and the code before data (higher scope) has declared a variable of the same name (after the colon).

Instead of typing:
 
    data {
      email: email
    }

Instead type:

    data {
      email
    }

If you have not destructured the variable into its own object, you still need to include the colon:

    data {
      email: args.email
    }
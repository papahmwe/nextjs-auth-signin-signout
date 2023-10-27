### Zod

Zod = TypeScript-first schema declaration, validation library

- to eliminate duplicative type declarations
- declare a validator once and Zod will automatically infer the static TypeScript type
- to compose simpler types into complex data structures

### Schema

Schema = the organization or structure for a database

### useRouter

To access the router object inside any function component in your app,
can use the useRouter() hook.

## Authentication

!! Have to use Next-Auth

### NextAuth.js

- A complete open-source authentication solution for Next.js applications.
- Next.js also has an Authentication package called Next Auth that makes it easy to add authentication to a Next.js app.

#### Why use next auth?

- Next Auth is a secure authentication system for Next.js applications.
- It is based on JSON Web Tokens (JWT) and provides authentication and authorization.

### To add NextAuth.js to a project

- need to create a file called route.ts in the /app/api/auth/[...nextauth] directory (dynamic route handler for NextAuth)

Note;

- to keep or store the current authenticated user data, use session() method
- to share session object across components or to get the login state of our users and render user details on the frontend of our app, need to wrap around our components with SessionProvider

Note;

- NextAuth မှာ Provider ကို CredentialsProvider သုံးထားတယ်
- CredentialsProvider ရဲ့ အရေးကြီးဆုံးအပိုင်းက authorize() function ဖြစ်တယ်
- authorize() function ထဲမှာ user ကို ရှာရန် logic ကို ထည့်ပေးရတယ်

### Fixing the next-auth no secret warning

- To fix the next-auth no secret warning, have to create NEXTAUTH_URL (eg:http://localhost:3000) and NEXTAUTH_SECRET(eg: lsdkmlskdmflksdkskmsdnkj) on .env
  Note;
- the URL is your domain and the secret is any hash

### getServerSession() in NextAuth

To call from the server-side i.e;

- in Route Handlers,
- React Server Components,
- API routes or in getServerSideProps,

to retrieve the session object, use getServerSession()

If callbacks.jwt or callbacks.session changed something,it can update the cookie expiry time and the session content.

It requires passing the same object you would pass to NextAuth when initializing NextAuth.js.

### Callback

- Asynchronous functions to control what happens when an action is performed.

- Powerful, involving JSON Web Tokens to implement access controls without a database and to integrate with external databases or APIs.

- To pass data such as an Access Token or User ID to the browser when using JSON Web Tokens, you can persist the data in the token when the jwt callback is called, then pass the data through to the browser in the session callback.

- It can set after the providers list, inside it, have to set database or JWT.

### JWT callback

- This callback is called whenever a JSON Web Token is created (i.e. at sign in) or updated (i.e whenever a session is accessed in the client). The returned value will be encrypted, and it is stored in a cookie.

- As with database persisted session expiry times, token expiry time is extended whenever a session is active.

### Session callback

- The session callback is called whenever a session is checked.

Note;

- When using database sessions, the User (user) object is passed as an argument.
- When using JSON Web Tokens for sessions, the JWT payload (token) is provided instead.

- If you use JWT or database sessions,

1. token: the JWT token for this session
2. session: the session object from your adapter

### useSession()

- to check user login state and obtain session information, use the useSession() Hook (a React Hook)
- if a session exists, conditionally render the signin and signout links

Note;
useSession() returns an object containing two values: data and status

#### data

data: this can be three values: Session / undefined / null

Session
\
in case of success, data will be Session.

undefined
\
when the session hasn't been fetched yet, data will be undefined

null
\
in case it failed to retrieve the session, data will be null

#### status

status: enum mapping to three possible session states: "loading" | "authenticated" | "unauthenticated"

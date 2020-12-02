# ifdefined

Install hugo:
```
brew install hugo
```

Start dev server:

```
hugo server -D
```

Start sass compilation:
```
sass --watch scss/main.scss:static/styles/styles.css
```

### Deploymen

With NodeJS utility [http-server](https://www.npmjs.com/package/http-server).

Install it with
```
npm install http-server -g
```

Start the server in the root directory and it will serve the `/public` directory:
```
http-server
```

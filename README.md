# Learning React and NextJS

## Steps to build site from empty folder

1. Install packages
```bash
npm init -y
npm i react react-dom, next
```

2. Add scripts to `package.json `
```json
"dev": "next",
"build": "next build",
"start": "next start"
```

3. Add `pages` folder and `index.js` file.  NextJS will automatically route to any page placed in this folder.

```js
const IndexPage = () => {
    return (
        <div>Hello World!</div>
    )
}

export default IndexPage;
```

4. Build and run application

```bash
npm run dev
```

5. Optional - If wanting a template file added to all pages, add `_document.js` to the `pages` folder

```js
import Document, { Head, Html, Main, NextScript } from "next/document";

class MyDocument extends Document {
  static async getInitialProps(ctx) {
    const initialProps = await Document.getInitialProps(ctx);
    return { ...initialProps };
  }

  render() {
    return (
      <Html>
        <Head>
          <meta charSet="utf-8" />
          <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css"/>
          <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.0/css/all.css"/>
          <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css" />
          <link rel="stylesheet" href="css/styles.css" />
        </Head>
        <body>
          <Main />
          <NextScript />
        </body>
      </Html>
    );
  }
}

export default MyDocument;
```

6. Optional - Any file or folder placed in `public` folder will be downloadable from the app.  For example you would create a `styles.css` file under public to use as the website wide CSS if referencing it from `_document.js`.
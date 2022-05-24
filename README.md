# Learning React and NextJS

## Steps to build MVP website from empty folder

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

5. Test using URL http://localhost:3000

## Steps to add common additional functionality to website

6. Add a template file `_document.js` to the `pages` folder.  This contect will be added to all pages.

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
          <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/css/bootstrap.min.css" integrity="sha384-0evHe/X+R7YkIZDRvuzKMRqM+OrBnVFBL6DOitfPri4tjfHxaWutUpFmBp4vmVor" crossorigin="anonymous"/>
          <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/fontawesome.min.css" />
          <link rel="stylesheet" href="css/styles.css" />
        </Head>
        <body>
          <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.0-beta1/dist/js/bootstrap.bundle.min.js" integrity="sha384-pprn3073KE6tl6bjs2QrFaJGz5/SUsLqktiwsUTF55Jfv3qYSDhgCecCxMW52nD2" crossorigin="anonymous"></script>
          <script src="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/js/fontawesome.min.js"></script>
          <Main />
          <NextScript />
        </body>
      </Html>
    );
  }
}

export default MyDocument;
```

7. Any file or folder placed in `public` folder will be downloadable from the app.  For example you would create a `styles.css` file under public to use as the website wide CSS if referencing it from `_document.js`.

8. If using GIT for source control create `.gitignore` file

```
/node_modules
/.next
```

9. Add a second page named `routed-page.js` to show routing. Test using URL (http://localhost:3000/routed-page).

```js
const RoutedPage = () => {
    return (
        <div>Routed successfully to another page</div>
    )
}

export default RoutedPage;
```

10. Add a component folder named `components` and a file named `simple-label.js` to be used to replace some of the functionailty of the `routed-pages.js` page.

```js
const SimpleLabel = ({label}) => {
    return (
        <div>{label}</div>
    )
}

export default SimpleLabel;
```

10. Add the component to the `routed-pages.js` page adding an `import` and replacing the `<div>`.

```js
import SimpleLabel from "../src/components/simple-label"

const RoutedPage = () => {
    return (
        <SimpleLabel label='Routed successfully to another page and loaded component'></SimpleLabel>
    )
}

export default RoutedPage;
```

The rest is standard React.  Happy coding!

 ## Thoughts

 * It is easier to start a NextJS React project than an Angular project due to less boilerplate code requirements.
 * Better enforcement of component encapsulation where props are passed in and out of components more naturally than Angular's @input, @output methods.
   * Can pass in a callback function as easily as a typical JavaScript object or basic data type

 ## Questions
 
 ### How do we control what is rendered client side vs server side?

 Would prefer to spread the work across all the clients rather than just a few servers.

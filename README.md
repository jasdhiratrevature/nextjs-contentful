This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `pages/index.js`. The page auto-updates as you edit the file.

[API routes](https://nextjs.org/docs/api-routes/introduction) can be accessed on [http://localhost:3000/api/hello](http://localhost:3000/api/hello). This endpoint can be edited in `pages/api/hello.js`.

The `pages/api` directory is mapped to `/api/*`. Files in this directory are treated as [API routes](https://nextjs.org/docs/api-routes/introduction) instead of React pages.

This project uses [`next/font`](https://nextjs.org/docs/basic-features/font-optimization) to automatically optimize and load Inter, a custom Google Font.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/deployment) for more details.

---
### Branch Name : 01-InitialSetUp

1. Once we have create a next js project it is time to do some initial setup , like creating a layout providing a style and updating the index.js and other files.
2. Create a folder `component` in the root directory inside this directory create a `Layout` component by creating a file Layout.js
3. Update the `_app.js` file and enclose the code inside the `Layout` component.
4. Create a folder `recipes` inside the pages folder and create a file inisde it name the file `[slug].js` the component name `RecipeDetails`
5. Update the  `index.js` , remove the content that is present and create a new component `Recipes` for the page
6. Finally execute the dev server and view your site on browser `localhost:3000`
7. update the global.css as well in the styles folder

---

### Branch Name : 02-Contentful_Models

1. Having set up the initial NextJS project, it is time to create our content model in the Contentful CMS.
2. Login to your Contentful CMS and create your content model.
3. We are going to create a content model/type named `Recipe` for the recipe with the following fields

    - Title --> Short Text --> Required, Unique
    - Slug --> Short Text --> Required, Unique, Pattern (^[a-z0-9]+(?:-[a-z0-9]+)*$)
    - Thumbnail --> Media --> Image Only
    - Featured Image --> Media --> Image Only
    - Ingredients --> Short Text, List --> as Tag
    - Cooking Time --> Number
    - Method --> Rich Text

4. Once the Recipe Type is created, go ahead and add some data, for images please upload and publish some images.

---

### Branch Name : 03-Contentful_Client

1. Now we are going to show the data stores in our contentful cms on our next js application.
2. to do this we are going to use the contentful client package whci we can install with npm.
3. Open up a new terminal and then tey the following command
` npm install contentful`. 
4. This package we can use in our application to connect to our contentful accoiunt and then grab data from it.
5. We want to get data from our index.js page, so open up the index.js page and this is where we are going to connect to our contentful.
6. create and export the getStaticProps() function from nextjs in our index.js
7. This function is used to grab some data and onject that data to the props into our components so that we can render it in the browser.
8. The createClient function makes a connection to the ContentfulCMS.
9. The createClient functions needs and object as parameter, the content of the object are space id and accessToken
10. Grab the space id and accessToken from your contentful instance.
11. Its is always a bad idea to have the space ID and accesstoken in the code, hence move the space id and accestoken to enviornment variable in an .env.local file in the root of the project.

### Note : Please restart the dev server once changes are made to the .env file

12. use the getEntries() nethod from the contentful client and return the recipes as props.
13. Pass the props to the Recipe component

---

### Branch Name : 04-Outputting_Recipe_Data
1. Let  us now display the data fetched from the getEnteries() in to our Component.
2. We can now iterate over the recipe data uisng a map function and display it, but we want to keep our Home component , i.e. index.js clean.
3. We will create a seperate component `RecipeCard` in the component folder and use it in the Recipes/Home component.
4. So let us make that component `RecipeCard`
5. Also go ahead and click on the link cook-this for any of the recipe. 
6. You will be taken to the Recipe Details page. Notice the url at the end, that's the slug.

---

### Branch Name : 05-Using_Images_From_Contentful
1. To output the image we will use the built in `Image` component from `NextJS`, which auto optimizes images for us.
2. Add the Image component and add the src , width , height props for the component.
3. Once done , save your page, you will get an error
    `hostname "images.ctfassets.net" is not configured under images in your` `next.config.js`
4. Go ahead and configure the `next.config.js` file
5. Restart the dev server and view the output.

---



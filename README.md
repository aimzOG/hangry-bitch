# hangry-bitch

> hangry-bitch is a recipe site

## Build Setup

``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).



If you don't have a course project repo from lesson01 or want to start fresh, go ahead and create a new repo -- just be sure to add Patrick and I as collaborators in the Settings. 
Make sure the documents folder from lesson01 is present in the root of the repo with your original proposal (and with the addition of the SEO doc for lesson10 when submitted)
Create a new Nuxt project in your repo with `yarn create nuxt-app my-project-name` 
Follow the assignment09 instructions for the prompts (make sure to add the required scss packages as noted)
After you've created the Nuxt project, move all of the generated files/folders into the root of your repo. In other words, in the root of your repo should be the Nuxt files (package.json, assets, components, pages) as well as your documents folder you created and/or migrated. See the attached screenshot for how the repo root should look like.
Once your Nuxt project is generated and working, you'll want to migrate over your previous Vue CLI files over to Nuxt
Nuxt is very similar, so we'll just have to move stuff to the right spots and update the file pathing
Don't worry about the compilation errors or even running the dev server at first, just focus on copying the files over and updating the pathing
Start with your previous App.vue -- this will go into 'layouts/default.vue'. You'll want to change the <router-view /> tag to the <nuxt /> tag, and replace any <router-link> or <b-link> with <nuxt-link>
Next, move your 'view' components (your page components) into the 'pages' directory. You can create folders to generate the routes, so 'pages/about/index.vue' will automatically route to '/about' or 'pages/overview/about.vue' will route to '/overview/about'. Feel free to structure the routing/pages as you'd like
No need to bring over your router files, Nuxt does this for you
Now, bring over your other components into the 'components' directory.
For any main.scss/other scss, JavaScript files like mixins/filters, and image/video files -- go ahead and migrate all of those files into the 'assets' directory. Ideally you would have folders for your different assets, so maybe you have an images, a mixins, and a scss folder, and within those the respective files.
At this point you should have all of your required files in the project, now you'll need to update the pathing
Nuxt uses the @ alias to reference the root of the project, so if you put your components in the components folder and were importing them previously like "import MyComp from '@/components/myComp.vue'" then it should just work
Go through your pages/components and update the import paths (and require paths for images) to match your new structure
If you were importing mixins/filters make sure those path updates are reflected as well
Make sure your asset files and your references to them use the same case. So, if you have 'assets/img/MyImg.jpg' and reference it in a component as 'assets/img/myimg.jpg', it will probably work on your local machine but will break in the deployment
Once you've got your Nuxt app running and working as expected, try connecting the repo to Netlify to see if you have any issues with the build

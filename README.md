# hello world and hello universe

This project contains two Vue components, created with Typescript enabled in the Vue project set-up.

## Usage

If the project was published to npm, you could include it using npm install _project-name_. As it is, you can include it by cloning the repo, running ```npm run library``` and then ```npm link PATH_TO_REPO```.

## How it was created

The project was created by the following:

```vue create LIBRARY_NAME```

Add new option to scripts section in package.json:

```"library": "vue-cli-service build --target lib --name LIBRARY_NAME src/main.ts"```

LIBRARY_NAME is used in the creation of the distribution files. I'm not sure if it is used elsewhere.

'src/main.ts' is the entry point for the build.

Also in package.json add, at the top level:

 ```"main": "./dist/HelloWorld.common.js",```

The src/main.ts file was edited and the contents entirely replaced with:

```
import HelloWorld from './components/HelloWorld.vue';
import HelloUniverse from './components/HelloUniverse.vue';

export {
  HelloWorld,
  HelloUniverse,
};
```

I'm not sure if there is a more Typescripty way of doing the adove.

These exports are the components that you will import into your project.

I am using the default HelloWorld component and HelloUniverse, which is just a duplication of HelloWorld with some different text.

In the root of the project I have included a '.eslintignore' file with '**/*' as the contents. This seems to prevent eslint errors when the distribution files are imported into a JS project. I have done this on the basis that I assume that another project should not be linting a third party library.

## Issues

Importing into a Typescript project works, but in VSCode it gives a warning that a type declaration file is missing. I have yet to work out a successful way to specify this.


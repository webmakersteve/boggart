Boggart
=======

Big file package management system hookable into storage APIs.

The intent of this package is to be a cli and node package tool for managing front-end big data dependencies. GitHub says it themselves in their https://help.github.com/articles/working-with-large-files. The TL;DR is don't. 

Well, that would be perfectly fine but we don't have a distributed system for managing front-end large dependencies. And there's probably a reason why: they're huge. So the idea is to levy a service that already specializes in dealing with distributed large files and integrate it into developer workflow to increase productivity and fix the headaches of dealing with big data.

## Support

This cli will come out with Dropbox support, as it is my cloud of choice. But anything with an HTTP API will be supported provided bindings and created. A how-to guide on doing that will be created in the future.

Here's an example concept:

```javascript

/* package.json */
...
"postinstall": "boggart pull dropbox://stephen@password:/public/boggart.bog public/assets",
...

```

Now when you run npm install it will pull the files or archive from the directory, decompress and open an archive - if specified, and place them where you specify. If you don't specify where to put them it will default to the working directory, which you probably don't want.

Boggart can also be run straight from its cli, naturally. 

```shell
boggart init --working-tree=public/assets
- Initialized empty boggart repository
boggart remote set origin dropbox://stephen@password:/public/boggart.bog
- Set remote to use dropbox.
boggart pull
...
```

## Optimization

Naturally, HTTP requests are expensive. You can optimize the speed and bandwidth boggart uses by archiving your files before hand, but we do not force this on you.

### Inspiration

```apt-get``` for teaching me to love package managers

```pacman``` for teaching me to love package managers even more

```bower``` for showing the utility of front-end package managers

```git``` for showing that deployment doesn't need to be so *terrible*

I hope when this comes to life people will enjoy it :)

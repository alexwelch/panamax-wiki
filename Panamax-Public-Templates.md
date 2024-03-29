##What are the Panamax Public Templates

The [Panamax Public Template repository](https://github.com/CenturyLinkLabs/panamax-public-templates) contains Panamax templates available to all users of Panamax. They have been crafted with certain standards for the image and template, to ensure their functionality. Learn more about what we think makes a good image and template below.

##What we think makes a good image

* **Be specific** - When creating your own image, try to be as specific as you can when it comes to applications or packages. This gives you more control of the functionality of the image and gives a better success rate if someone takes your image and tries to build it themselves. You don't want to get the latest of an app only to have it work when you pulled it, but break a couple months later due to an incompatibility. Opt for a specific version rather than just 'stable'. Image creation should also be about reliability and consistency.

* **Be flexible** - Between mounted volumes (-v), environment variables (-e) and command arguments, Docker gives the user many ways to pass data into a running container. Make your image more flexible by using these features to allow users to configure the behavior of the service running inside the container.

* **Know your sources** - When you use `FROM` in your Dockerfile, your base image is going to come with some baggage. Everything from ports, environmental variables, volumes and the CMD can be propagated down to your image. It's always best to do your homework on exactly what you are inheriting. The best source of information for an image is its Dockerfile but if you find an image with no published Dockerfile you can use a tool like  [dockerfile-from-image](https://registry.hub.docker.com/u/centurylink/dockerfile-from-image/) to reverse engineer a Dockerfile from an image. It's good to use official images from Docker when you can; however, you sometimes have to hunt around for the associated Dockerfile (many of the official images can be found at [https://github.com/docker-library](https://github.com/docker-library))

* **Optimize your image** - See <a href="http://www.centurylinklabs.com/optimizing-docker-images/">Brian DeHamer's blog post</a> on great ways to keep your image size under control. His section on chaining commands is worth the read. You'd be surprised how unwieldy an image can get! Downloading 200MB vs. 2GB is a BIG difference on time and needed storage space.

* **Publish your Dockerfile** - The Docker Registry has a lot of goodness, but one badness is that Dockerfiles are not always published, making image construction a black hole. Here at CenturyLinkLabs, we always publish our Dockerfile and supporting files into a Github repo and then link it to the Docker Registry using their automated builds feature. 

##What we think makes a good template.

* **Documentation is essential!** - We generally break our documentation down to a few sections : System Requirements - How much horsepower will it need? Setup - Do environmental variables need to be added? Post-Run Instructions - Is an username and password needed to access the app? Resources - Have a blog about your template?

* **Be specific, again!** - We try to avoid the 'latest' tag when we can for the images we reference in our templates. This cuts down on unexpected changes that could break your app.

* **Whats in a name?** - Make sure your name and description describes your template well. We use this for searching and it lets others know what your app provides.

* **Use the power of Panamax!** - Avoid hardcoded Docker specifics in your images. The power of Panamax is the ability to make these configurations flexible.

##Submit a Template!

**\--> NOTE: This process is to submit template to the official template repository, if you want to enter the Panamax App Template Challenge (Contest) please be sure to follow the instructions from:** [http://panamax.io/contest](http://panamax.io/contest)

1. Fork the official the official Panamax Template Repository from [https://github.com/CenturyLinkLabs/panamax-public-templates](https://github.com/CenturyLinkLabs/panamax-public-templates) to your personal GitHub account.

2. Press **Save as Template** in Panamax for your new application and save your template to your forked panamax-public-templates repository.

3. Once your template is ready, go to GitHub and submit a pull request from your forked panamax-public-templates repository.
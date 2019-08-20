# Container Scanners

Containers help solve the “well it worked on my laptop” issue that was quite prevalent in the past. Developers can now define the exact versions of dependencies that have been tested to work alongside their applications. There is however a dark side to this. In the old days you may have had a team of operations and security people responsible for upgrades. Today we have thousands of images with who knows what inside that never get updated.

This security issue became headline news a few years ago when it emerged that a large proportion of the images on Dockerhub contained vulnerabilities. Docker went to great lengths to add new features to try to combat this massively negative publicity. More recently I read an article that said backdoored images on Dockerhub had been downloaded 5 million times before removal.

Today we’ll compare some container vulnerability scanning applications that you can run yourself. This comparison does not include any SaaS applications. The majority are free and opensource with the exception of Twistlock.

## Nice

**Aqua Microscanner** (<https://www.aquasec.com/>)

Aqua make some cool open source security software. It takes a different approach to scanning than the other options. To enable scanning you simply add 3 lines to a Dockerfile. The free version does come at the cost of providing an email address. There is also a paid enterprise version that adds more features.

The scan was very quick and this is probably the simplest way to add vulnerability scanning to your pipelines.

**Twistlock** (<https://www.twistlock.com/>)

This is paid software. I was curious to see what vulnerabilities it would find versus the free options. Installation of Twistlock wasn’t particularly difficult. We bundled it into a container and execute scans as part of our pull request builds.

## Others

- Clair
- Anchore Engine
- Twistlock
- Dagda
- OpenSCAP

## Recap

Aqua Microscanner and Twistlock only take a couple of minutes to run which is perfect for adding to a pipeline.

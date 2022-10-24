# MMB DTP

[![pages-build-deployment](https://github.com/mmbdtp/mmbdtp.github.io/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/mmbdtp/mmbdtp.github.io/actions/workflows/pages/pages-build-deployment)

Website for the MMBdoctoral training program


# Deploy locally with docker 

``` 
export JEKYLL_VERSION=3.5
docker run --rm   --volume="$PWD:/srv/jekyll"  --publish [::1]:4000:4000 jekyll/jekyll:$JEKYLL_VERSION  jekyll build
docker run  --name mmbdtp --volume="$PWD:/srv/jekyll" -p 3000:4000 -it jekyll/jekyll:$JEKYLL_VERSION jekyll serve --watch --drafts
```

The development build is available on http://localhost:3000 

Use `docker start` to start the service, once the container is built.


---

Based on Course-in-a-Box, which was 
Course-in-a-Box was built by [Peer 2 Peer University](https://www.p2pu.org) using the [P2PU Jekyll course template](https://github.com/p2pu/jekyll-course-template) and shared under an MIT License.

Course content ("Modules") are shared under a [CC BY-SA 4.0 license](https://creativecommons.org/licenses/by-sa/4.0/).

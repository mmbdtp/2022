# MMB DTP

[![pages-build-deployment](https://github.com/mmbdtp/mmbdtp.github.io/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/mmbdtp/mmbdtp.github.io/actions/workflows/pages/pages-build-deployment)

A problem-based learning curriculum for the **Microbes, Microbiomes and Bioinformatics** doctoral training program

### Programme

6 weeks programme, with the week start date reported:

* 07 Nov 2022, **Linux and the Command Line**, Mark Pallen and Andrea Telatin
* 14 Nov 2022, **Creating and handling sequences**, Dave Baker 
* 21 Nov 2022, **From sequence to consequence**, Nabil Alikhan and Mark Pallen
* 28 Nov 2022, **Comparative genomics**, Gemma Langridge and Andrew Page
* 05 Dec 2022, **Metagenomics**, Chris Quince
* 12 Dec 2022, **Functional analysis**, Mark Webber and Cynthia Whitchurch


### Deploy locally with docker 

``` 
export JEKYLL_VERSION=3.5
docker run --rm   --volume="$PWD:/srv/jekyll"  --publish [::1]:4000:4000 jekyll/jekyll:$JEKYLL_VERSION  jekyll build
docker run -p 80:4000 --name mmbdtp --volume="$PWD:/srv/jekyll" -it jekyll/jekyll:$JEKYLL_VERSION jekyll serve --watch --drafts
```



The development build is available on http://localhost:4000 

Use `docker start` to start the service, once the container is built.


---

Based on Course-in-a-Box, which was 
Course-in-a-Box was built by [Peer 2 Peer University](https://www.p2pu.org) using the [P2PU Jekyll course template](https://github.com/p2pu/jekyll-course-template) and shared under an MIT License.

Course content ("Modules") are shared under a [CC BY-SA 4.0 license](https://creativecommons.org/licenses/by-sa/4.0/).

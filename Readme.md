
## Docker Image
shashibanger/jekyll:0.1 can be built using [Dockerfile](https://github.com/shashi-banger/usefull_dockers/blob/master/jekyll/Dockerfile)

## To run local server
docker run -it --rm --network host --privileged -v `pwd`:/data/ shashibanger/jekyll:0.1 bash

### Inside docker following

```
cd /data/
bundle exec jekyll serve
```


## To run local server
docker run -it --rm --network host --privileged -v `pwd`:/data/ shashibanger/jekyll:0.1 bash

### Inside docker following

```
cd /data/tech-notes/
bundle install
bundle exec jekyll serve
```

# texlive_docker_cn
a cn version cloned from https://gitlab.com/islandoftex/images/texlive.git


# Docker TexLive in China on Windows
first build point_release_image, it will use about an hour to download files and create docker images, so it can be treated as a point release imgage. You should rebuild this images only if there is big improvement in TeXLive 

second build olling_release_image, it is based on point_release_image and do update, and tag newly built image as `texlive_local_rolling_build:latest`, it must be build-quickly and contain refresh packages. 

after rebuild，remeber to delete old image since it's big.

## how to build

```
docker build  --platform linux/amd64 -t texlive_local_point_build:latest . -f Dockerfile.cn_point_release_image 


docker build  --platform linux/amd64 --pull=false -t texlive_local_rolling_build:latest . -f Dockerfile.cn_rolling_release_image


```

## usage 

replace command by `wsl docker run ...` in your TeX build-system/text-editor/ide, such as  `wsl docker run -i --rm --name latex -v "$PWD":/usr/src/app -w /usr/src/app texlive_local_rolling_build:latest latex -src -interaction=nonstopmode %.tex` instead of `latex -src -interaction=nonstopmode %.tex`. 

open `Docker-Desktop`, and do tex job.






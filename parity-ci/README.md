# Gitlab setup for Heavy projects.
For now, GitLab's only caching cycle is: 
- zip everything within the set path
- upload
- download
- unzip
This seems OK for web projects, for non-compilable languages and generally for small code bases.

But when the application takes minutes to compile, you start noting a tradeoff of this type of caching:
- zipping and uploading the cache takes time comparable with the compilation time
- downloading and unzipping takes this time one more time
- this happens every CI job
And if the compilation without caching took 5 minutes, this strategy makes it 15 when you decide to cache all the dependencies. 
Of course it's not worth it.
#TODO
And what if you want to store compilation cache? It's capable to reduce the compilation times by four!
Are you sure? It grows fast and can take tens of Gigs!

# Caching with Docker volumes
Gitlab allows to set up volumes for your docker containers in the gitlab-runner's config:
#TODO
Volume is fast, it does not take time for loading and zipping back and forth, lives locally, takes cheap local drive space and just plugs in when you need so.

# Rust
## CARGO_HOME
Downloads
Dependencies
Data race
## CARGO_TARGET
Zero-compilation time on repeats
## Sccache
Link
Short desc
How to set up locally
How to set up for CI
Distributed features
Data race (none, bug)
## Incremental compilation
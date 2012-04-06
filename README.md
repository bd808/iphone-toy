Example iPhone Offline Site
===========================

Just playing around with a tool chain and template for developing applications
optimized for iphone deployment.

Building
--------
* Go install [rbenv][] and [ruby-build][] if you don't have them.
* Install ruby 1.9.2: `rbenv install 1.9.2-p290`
* Install required gems using bundler:

    gem install bundler
    rbenv rehash
    bundle install

Compass was setup like this:

    compass create \
      --sass-dir assets/sass \
      --css-dir assets/css \
      --images-dir assets/img \
      --javascripts-dir assets/js

---
[rbenv]: https://github.com/sstephenson/rbenv#section_2
[ruby-build]: https://github.com/sstephenson/ruby-build

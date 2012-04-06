Example iPhone Offline Site
===========================

Just playing around with a tool chain and template for developing applications
optimized for iphone deployment.

---
rbenv
https://github.com/sstephenson/rbenv#section_2
https://github.com/sstephenson/ruby-build
rbenv install 1.9.2-p290

rvm
http://octopress.org/docs/setup/rvm
rvm install 1.9.2 && rvm use 1.9.2

gem install bundler
rbenv rehash
bundle install

compass create --sass-dir assets/sass --css-dir assets/css --images-dir
assets/img --javascripts-dir assets/js



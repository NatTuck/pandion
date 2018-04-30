
task :serve do
  system("bundle exec jekyll s")
end

task :build do
  system("bundle exec jekyll build")
end

task :ship do
  Rake::Task[:build].execute
  system("rsync -avz --delete _site/ nat@coyote.ferrus.net:~/www/pandion.ferrus.net/")
end


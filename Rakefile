desc "Build the gem"
task :gem do
  sh "bundle exec gem build motion-cocoapods.gemspec"
  sh "mkdir -p pkg"
  sh "mv *.gem pkg/"
end

task :clean do
  FileUtils.rm_rf 'pkg'
end

desc "Install dependencies needed for development"
task :bootstrap do
  sh "git submodule update --init"
  sh "bundle install"
end

desc "Run all the specs"
task :spec do
  #sh "env COCOAPODS_VERBOSE=1 bundle exec bacon #{FileList['spec/*_spec.rb'].join(' ')}"
  FileList['spec/*_spec.rb'].each do |spec|
    # execute spec separately to make sure that reset data of App.config.
    sh "bundle exec bacon #{spec}"
  end
end

desc "Run specs automatically"
task :kick do
  sh "kicker -c -e 'rake spec'"
end

task :default => :spec

desc 'build the static site'
task :build do
  sh 'bundle exec middleman build'
end

desc 'deploy build directory to github pages'
task deploy: :build do
  puts 'Deploying branch to Github Pages'
  sha = `git log | head -1`.strip.split(' ').last
  cp_r '.nojekyll', 'build/.nojekyll'
  cd 'build' do
    system 'git add .'
    system 'git add -u'
    message = "Site updated at #{Time.now.utc} (#{sha})"
    system "git commit -m \"#{message}\""
    system 'git push origin master'
  end
  puts 'Github Pages deploy complete'
end

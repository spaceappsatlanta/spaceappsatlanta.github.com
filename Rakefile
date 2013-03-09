desc 'deploy build directory to github pages'
task :deploy do
  puts 'Deploying branch to Github Pages'
  sha = `git log | head -1`.strip.split(' ').last
  cp_r '.nojekyll', 'build/.nojekyll'
  cd 'build' do
    system 'git add .'
    system 'git add -u'
    message = "Site updated at #{Time.now.utc} (#{sha})"
    puts "Commiting: #{message}"
    system "git commit -m \"#{message}\""
    puts 'Pushing generated website'
    system 'git push origin master'
    puts 'Github Pages deploy complete'
  end
end

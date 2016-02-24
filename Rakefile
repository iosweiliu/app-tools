task :default => :test

VERSION = '1.1.2'
BUILD = '20160224.2'

task :test do
  Dir.glob('./test/test_*.rb').each { |file| require file}
end

task :vamper do
  `vamper -u`
  `git add :/`
  `git commit -m 'Update version info'`
  puts "Updated version to #{VERSION}-#{BUILD}"
end

task :release do
  `git tag -a 'v#{VERSION}' -m 'Release v#{VERSION}-#{BUILD}'`
  puts "Pushing tags to GitHub..."
  `git push --follow-tags`
  `rm *.gem`
  `gem build app-tools.gemspec`
  puts "Pushing gem..."
  `gem push app-tools-#{VERSION}.gem`
end

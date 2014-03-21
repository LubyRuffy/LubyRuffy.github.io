namespace :lubyr do
  desc "call jekyll build"
  task :b do
    if __FILE__.include? 'lubyruffy_jekyll'
      puts %x{jekyll build}
    end
  end

  desc "copy files to github pages static files"
  task :c => :b do
    if __FILE__.include? 'lubyruffy_jekyll'
      puts %x{pwd}
      #copy public files to ../LubyRuffy.github.io
      puts %x{cp -r ./public/* ../LubyRuffy.github.io/}
      puts %x{cd ../LubyRuffy.github.io/ && rake lubyr:gitpush m='#{ENV['m']}'}
    end
  end

  desc "call git push"
  task :gitpush => :c do
    if !ENV['m']
      puts "error: need input commit memo!"
      exit
    end
    puts %x{git add -A}
    puts %x{git commit -m #{ENV['m']} }
    puts %x{git push}

  end
end

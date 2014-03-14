namespace :lubyr do
  desc "call jekyll build"
  task :b do
    puts %x{jekyll build}
  end

  desc "call git push"
  task :gitpush => :b do
    if !ENV['m']
      puts "error: need input commit memo!"
      exit
    end
    puts %x{git add -A}
    puts %x{git commit -m #{ENV['m']} }
    puts %x{git push}

    if __FILE__.include? 'lubyruffy_jekyll'
      #copy public files to ../LubyRuffy.github.io
      puts %x{cp -r ./public/* ../LubyRuffy.github.io/}
      puts %x{cd ../LubyRuffy.github.io/ && rake lubyr:gitpush m='#{ENV['m']}'}
    end
  end
end

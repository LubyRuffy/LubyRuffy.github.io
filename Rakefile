namespace :lubyr do
  desc "call jekyll build"
  task :b do
    puts %x{jekyll build}
  end

  desc "call git push"
  task :gitpush => :b do
    puts %x{git add -A}
    puts %x{git commit -m #{ENV} }
    puts %x{git push}
  end
end

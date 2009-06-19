Deploying
---------

### Error: :keep_releases not working
You've set :keep_releases but the old releases are not being deleted

### Action
You need to also specify the callback for the cleanup task in your deploy.rb

    after "deploy:update", "deploy:cleanup"
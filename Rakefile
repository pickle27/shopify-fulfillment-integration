require "sinatra/activerecord/rake"
require "./app"

task :server do
  SinatraApp.run!
end

task :clear_shops do
  Shop.delete_all
end

task :creds2heroku do
  Bundler.with_clean_env {
    api_key = `sed -n '1p' .env`
    shared_secret = `sed -n '2p' .env`
    secret = `sed -n '3p' .env`
    `heroku config:set #{api_key}`
    `heroku config:set #{shared_secret}`
    `heroku config:set #{secret}`
  }
end

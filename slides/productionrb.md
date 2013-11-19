###  production.rb

```Ruby
	config.serve_static_assets = true

	# Compress JavaScripts and CSS
	config.assets.compress = true

	# Setting compressor currently doesn't work (thx to @carhartl for the tip) https://github.com/rails/sass-rails/issues/104
	config.assets.css_compressor = :yui
	config.assets.js_compressor = :uglifier

	# Don't fallback to assets pipeline if a precompiled asset is missed
	config.assets.compile = false

	# Generate digests for assets URLs
	config.assets.digest = true

	# User cloudfront as deployment asset host
	# SET THIS AT THE END OF THIS GUIDE, 
	config.action_controller.asset_host = ENV['ASSET_HOST']
	```
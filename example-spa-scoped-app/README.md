This is a sample scoped app that uses npm.

Available npm scripts:

	$ npm run ci:build
	$ npm run ci:test

Please note that everytime you change dependencies in package.json, you'll need
to run "npm i" to update package-lock.json and check that in.

You may want to use [fswatch](https://github.com/emcrisostomo/fswatch) to continuously
build on changes:

	$ brew install fswatch
	$ fswatch -o -e '.*' -i 'src/main/plugins/.*' . | xargs -n1 -I{} mvn package

To run just one script, pass the `npm.script` property:

	$  fswatch -o -e '.*' -i 'src/main/plugins/.*' . | xargs -n1 -I{} mvn package -Dnpm.script=ci:test
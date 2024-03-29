# A simple NodeJS based service loader & scheduler.

Ever wanted to have multiple microservices run off of a single instance... then look no further.
With SSR you easily do just that

![david](https://david-dm.org/rohan-buchner/super-service-runner.svg)

## How to

Create either a single js file within the services folder, or a sub folder named the **same** as your intended app entry. eg:

~~~
../super-service-runner/services/bar.js
../super-service-runner/services/bar/bar.js
~~~

(Reason being if you need sub modules for a specific service, this will allow you to section off services, within their own directory)

Your service entry should only export a single function which will be invoked by the runner. This can be named or anonymous.

~~~
module.exports = function(config) {
  // your code here
}
// or
module.exports = function start(config) {
  // your code here
}
~~~

`services.config.yml` should contain an entry for your service (with the following at minimum). The properties you want to add to the config is dependent on your service requirements, but the scheduler itself only needs these:

~~~
foo:                       # matches your file name & or folder
  enabled: true            # if enabled or not
  cron: "*/1 * * * * *"    # cron schedule
~~~

...(again) in the above example foo is matched either the following by convention:

~~~
../super-service-runner/services/foo.js
// or
../super-service-runner/services/foo/foo.js
~~~


To start run (in the console):
`node start.js`

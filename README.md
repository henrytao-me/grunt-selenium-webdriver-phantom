# grunt-selenium-webdriver-phantom

> grunt-selenium-webdriver-phantom support

## Getting Started
This plugin requires Grunt `~0.4.4`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```
npm install grunt-selenium-webdriver-phantom --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```
grunt.loadNpmTasks('grunt-selenium-webdriver-phantom');
```

## Dependencies

```
npm install phantomjs --save-dev
npm install protractor --save-dev
./node_modules/protractor/bin/webdriver-manager update --standalone --chrome
```
(Belows are optional. Please see the example part)

```
npm install grunt-shell --save-dev
npm install grunt-protractor-runner --save-dev
```


## The "selenium_webdriver_phantom" task

### Overview
In your project's Gruntfile, add a section named `selenium_webdriver_phantom` to the data object passed into `grunt.initConfig()`.

```
grunt.initConfig({
  selenium_webdriver_phantom: {
	chrome: {

    },
    phantom: {
      options: {
        phantom: {}
      }
    },
    others: {
      
    }
  },
});
```

### Importance default stop selenium server grunt task (check )

```
grunt.registerTask('test:protractor', ['selenium_webdriver_phantom:stop']);

```

### Options

#### options.path
Type: `String`
Default value: `'{your_project}/node_modules/protractor/selenium/selenium-server-standalone-{auto_get_version}.jar'`

A string value that is used to run selenium server.

#### options.args
Type: `Array`
Default value: `[-Dwebdriver.chrome.driver={your_project}/node_modules/protractor/selenium/chromedriver]`

An array value that is used to run selenium server.

#### options.phantom
Type: `Object`
Default value: `undefined`

If you want to run selenium test with phantomjs, set this as {}.

#### options.phantom.path
Type: `String`
Default value: `'{your_project}/node_modules/phantomjs/bin/phantomjs'`

A string value that is used to run phantomjs server.

#### options.phantom.args
Type: `Array`
Default value: `['--webdriver', '8080', '--webdriver-selenium-grid-hub=http://127.0.0.1:4444']`

An array that is used to run phantomjs server.

### Usage Examples


```
grunt.initConfig({
  protractor: {
	options: {
	  keepAlive: true
    },
    all: {
      configFile: 'test-protractor.conf.js'
    }
  },
  shell: {
	protractor_webdriver_manager_update: {
	  options: {
		stdout: true
	  },
      command: require('path').resolve(__dirname, 'node_modules', 'protractor', 'bin', 'webdriver-manager') + ' update'
	}
  },
  selenium_webdriver_phantom: {
    chrome: {
	
    },
    phantom: {
      options: {
        phantom: {}
      }
    },
    custom_phantom: {
      options: {
        phantom: {
          path: '/path/to/phantomjs/bin/file',
          args: ['--webdriver', '9999']
        }
      }
    },
    others: {
      path: '/path/to/selenium/standalone.jar',
      args: ['-port', '8888']
    },
  },
});

grunt.registerTask('test:protractor', ['shell:protractor_webdriver_manager_update', 'selenium_webdriver_phantom:phantom', 'protractor', 'selenium_webdriver_phantom:stop']);

```



## Release History
_(Nothing yet)_

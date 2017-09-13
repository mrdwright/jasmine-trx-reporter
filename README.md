# jasmine-trx-reporter
A jasmine reporter that outputs the TRX file format for use with Visual Studio


#### Example use:
Within the config file add:

```var trx = require('jasmine-trx-reporter');```

Within the 'onPrepare' function of the protractor configuration, add the following:

     return browser.getCapabilities().then(function (capabilities) {

            var browserName = capabilities.get('browserName');
            var browserVersion = capabilities.get('version');

            var jasmineTrxConfig = {
                reportName: 'my favorite test suite',
                folder: 'testResults',
                outputFile: '',
                browser: browserName + "_" + browserVersion,
                groupSuitesIntoSingleFile: false
            };

            jasmine.getEnv().addReporter(new trx(jasmineTrxConfig));
        });
 
#### The constructor for the reporter takes a configuration object as seen above:
     reportName - the name of the report embedded within the trx file
     folder - optional folder to write trx results into
     outputFile - optional file name to write results to (Ex. myResults.trx).  If not outputFile is specificed it will be named according to the suite.
     browser - optional browser information to prepend to the outputfile name for compatibility with multicapabilities
     groupSuitesIntoSingleFile - groups all results into a single file.  This should be set to false if you want to shard your tests.
 
 
##### Example package.json dependencies
       "devDependencies": {
         "protractor": "5.1.2",
         "jasmine-trx-reporter": "2.2.3"
       }

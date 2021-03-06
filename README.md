Quickly publish a set of unstructured JSON objects into a Google spreadsheet that you specify.

# Installation

[![NPM Info](https://nodei.co/npm/object-to-google-spreadsheet.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.org/package/object-to-google-spreadsheet)

[![Build Status](https://travis-ci.org/ehab180hb/object-to-google-spreadsheet.svg?branch=master)](https://travis-ci.org/ehab180hb/object-to-google-spreadsheet)


## Example usage

```
const O2GS = require('object-to-google-spreadsheet');

// require your Google json credentials file
const creds = require('./creds');

const myReport = new O2GS(creds, '<Your docKey here>');

const options = {
    sheetName: 'My Awesome Report',
    rowName: 'person', // (optional) the key name of the base of your rows
    properties: 'properties', // (optional) the field containing your base's properties
    a1Field: 'details', // (optional) the value of the A1 field
    sort: true, // (optional) sort fields row alphabetically
    removeBase: false // (optional) if true, the base column won't be rendered in the sheet
};

// input must be an array of your objects
const docs = [
    {
        person : "John",
        properties : {
            Age: 25,
            Address : "16 main st."
        }

    },
    {
        person : "Jane",
        properties : {
            Age : 24,
            Hobbies : ["swimming", "Javascripting"]
        }

    }
];

// push your object to the sheet
myReport.push(docs, options)
.then(result => console.log(result))
.catch(err => console.log(err));

// using async/await
(async ()=> {
    try {
        await myReport.push(docs, options);
    } catch(err) {
        console.log(err);
    }
})();
```

## Example result

![updated sheet](https://i.imgur.com/pCi5BH9.png)


# docKey

- Every Google Sheet has a unique key in the URL
- https://docs.google.com/spreadsheets/d/{docKey}/

# Creds

1. Go to the Google [Developers Console](https://console.developers.google.com/cloud-resource-manager)
2. Select or Create Project
3. Dashboard > Enable APIs and Services > Enable the Drive API for your project
4. Credentials > Create Service Account Key
5. Select Json Key type and save the downloaded json file to your project
6. Once you have created the services account, you will have an email xxx@xxx.iam.gserviceaccount.com. **Go to your Google Sheets file and shared the edit permission to the email address.**
2. For more details, please refer to https://www.npmjs.com/package/google-spreadsheet

# Links
- https://developers.google.com/google-apps/spreadsheets/
- https://www.npmjs.com/package/google-spreadsheet
- https://www.npmjs.com/package/array-to-google-sheets


## Author

[Ehab Khaireldin](https://github.com/ehab180hb)


## License

This project is licensed under the MIT License and built for OneMeter.com

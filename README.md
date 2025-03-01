<!-- Make sure you edit doc/README.hbs rather than README.md because the latter is auto-generated -->

drivelist
=========

> List all connected drives in your computer, in all major operating systems.

[![Current Release](https://img.shields.io/npm/v/drivelist.svg?style=flat-square)](https://npmjs.com/package/drivelist)
[![License](https://img.shields.io/npm/l/drivelist.svg?style=flat-square)](https://npmjs.com/package/drivelist)
[![Downloads](https://img.shields.io/npm/dm/drivelist.svg?style=flat-square)](https://npmjs.com/package/drivelist)
[![AppVeyor status](https://img.shields.io/appveyor/ci/mderrier/drivelist/master.svg?style=flat-square&label=windows)](https://ci.appveyor.com/project/mderrier/drivelist/branch/master)

Notice that this module **does not require** admin privileges to get the drives in any supported operating system.

Supports:

- Windows.
- GNU/Linux distributions that include [util-linux](https://github.com/karelzak/util-linux) and [udev](https://wiki.archlinux.org/index.php/udev).
- Mac OS X.

When the user executes `drivelist.list()`, the module checks the operating
system of the client and executes the corresponding drive scanning script.

Examples (the output will vary depending on your machine):

```js
const drivelist = require('drivelist');

const drives = await drivelist.list();
console.log(drives);
});
```

***

Mac OS X:

```sh
[
  {
    device: '/dev/disk0',
    displayName: '/dev/disk0',
    description: 'GUID_partition_scheme',
    size: 68719476736,
    mountpoints: [
      {
        path: '/'
      }
    ],
    raw: '/dev/rdisk0',
    protected: false,
    system: true
  },
  {
    device: '/dev/disk1',
    displayName: '/dev/disk1',
    description: 'Apple_HFS Macintosh HD',
    size: 68719476736,
    mountpoints: [],
    raw: '/dev/rdisk0',
    protected: false,
    system: true
  }
]
```

***

GNU/Linux

```sh
[
  {
    device: '/dev/sda',
    displayName: '/dev/sda',
    description: 'WDC WD10JPVX-75J',
    size: 68719476736,
    mountpoints: [
      {
        path: '/'
      }
    ],
    raw: '/dev/sda',
    protected: false,
    system: true
  },
  {
    device: '/dev/sdb',
    displayName: '/dev/sdb',
    description: 'DataTraveler 2.0',
    size: 7823458304,
    mountpoints: [
      {
        path: '/media/UNTITLED'
      }
    ],
    raw: '/dev/sdb',
    protected: true,
    system: false
  }
]
```

***

Windows

```sh
[
  {
    device: '\\\\.\\PHYSICALDRIVE0',
    displayName: 'C:',
    description: 'WDC WD10JPVX-75JC3T0',
    size: 68719476736,
    mountpoints: [
      {
        path: 'C:'
      }
    ],
    raw: '\\\\.\\PHYSICALDRIVE0',
    protected: false,
    system: true
  },
  {
    device: '\\\\.\\PHYSICALDRIVE1',
    displayName: 'D:, F:',
    description: 'Generic STORAGE DEVICE USB Device',
    size: 7823458304,
    mountpoints: [
      {
        path: 'D:'
      },
      {
        path: 'F:'
      }
    ],
    raw: '\\\\.\\PHYSICALDRIVE1',
    protected: true,
    system: false
  },
  {
    device: '\\\\.\\PHYSICALDRIVE2',
    displayName: '\\\\.\\PHYSICALDRIVE2',
    description: 'Silicon-Power2G',
    size: 2014314496,
    mountpoints: [],
    raw: '\\\\.\\PHYSICALDRIVE2',
    protected: false,
    system: false
  }
]
```

Installation
------------

Install `drivelist` by running:

```sh
$ npm install --save drivelist
```

Documentation
-------------

<a name="module_drivelist..list"></a>

### drivelist~list()
**Kind**: inner method of [<code>drivelist</code>](#module_drivelist)  
**Summary**: List available drives  
**Example**  
```js
const drivelist = require('drivelist');

const drives = await drivelist.list();
drives.forEach((drive) => {
  console.log(drive);
});
```

Tests
-----

Run the test suite by doing:

```sh
$ npm test
```

Contribute
----------

We're looking forward to support more operating systems. Please raise an issue or even better, send a PR to increase support!

- Issue Tracker: [github.com/lelivrescolaire/drivelist/issues](https://github.com/lelivrescolaire/drivelist/issues)
- Source Code: [github.com/lelivrescolaire/drivelist](https://github.com/lelivrescolaire/drivelist)

Before submitting a PR, please make sure that you include tests, and that the linter runs without any warning:

```sh
$ npm run lint
```

Support
-------

If you're having any problem, please [raise an issue](https://github.com/lelivrescolaire/drivelist/issues/new) on GitHub.

License
-------

The project is licensed under the Apache 2.0 license.

[yaml]: http://yaml.org

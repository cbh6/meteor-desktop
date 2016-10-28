![Logo](meteor-desktop.png)

# WORK IN PROGRESS

# Meteor Desktop
###### aka Meteor Electron Desktop Client
> Build desktop apps with Meteor & Electron. Full integration with hot code push implementation.

```bash
 cd /your/meteor/app
 meteor npm install --save-dev meteor-desktop
 # you need to have mobile platform added
 meteor --mobile-server=127.0.0.1:3000
 
 # open new terminal

 npm run desktop -- init
 npm run desktop

 # or in one command `npm run desktop -- --init` 
```

### What is this?

This is a complete implementation of integration between `Meteor` and `Electron` aiming to achieve the same level of developer experience like `Meteor` gives. 
To make it clear from the start, this is a **desktop client** - it is just like your mobile clients with `cordova` - but for desktops with `Electron`. It also features a full hot code push implementation - which means you can release updates the same way you are used to.  

### Prerequisites

 - Meteor >= `1.3.4`<sup>__*1__</sup>
 - at least basic [Electron](http://electron.atom.io/) framework knowledge
 - mobile platform added to project<sup>__*2__</sup>  

<sup>__*1__ `1.3.3` is supported if you will install `meteor-desktop` with `npm >= 3`</sup>
<sup>__*2__ you can always build with `--server-only` so you do not actually have to have android sdk or xcode to go on with your project</sup>

## Documentation

### Starting - scaffolding

If you have not run the example from the top of this readme, first you need to scaffold a `.desktop` dir in which your `Electron`'s main process code lives.
To do that run: (assuming `npm install --save-dev meteor-desktop` did add a `desktop` entry in the `package.json scripts` section)
```bash
npm run desktop -- init
```
This will generate an exemplary `.desktop` dir. Lets take a look what we can find there:
```
    assets              <dir> # place all your assets here
    import              <dir> # all code you do not want to structure into modules  
    modules             <dir> # your desktop modules (check modules section for explanation)
      example           <dir> # module example
        index.js              # entrypoint of the example module
        example.test.js       # functional test for the example module
        module.json           # module configuration  
    desktop.js                # your Electron main process entry point - treated like a module
    desktop.test.js           # functional test for you desktop app
    settings.json             # your app settings
    squirrelEvents.js         # handling of squirrel.windows events
```

### What do you call a module?

A module is a encapsulated piece of code, that can have its own npm dependencies. Module's API is published in a form or IPC events

![High level architecture](high-level-arch.png)

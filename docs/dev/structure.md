# Codebase structure

## Paradigm

**Sokora aims to follow the Model-View-Controller programming paradigm**. If you like reading, you can check [the Wikipedia page for MVC](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller), but TL;DR:

- Views are what the user sees. They take data, present it, and offer buttons and stuff.
- Buttons and stuff call the controller, which is on a separate file. Controllers validate data and do business logic.
- Controllers that need to use the database or get data types refer to models, which are also separate on files.
- Models do database stuff and give their output back, simple enough.
- Controllers finish working and give data to the view for it to update.

Thus,

- Views can call controllers and controllers can call models, but never can a view call a model nor a model can call anything nor a controller can be inside of a view nor can everything be mixed up.

We’re not “purist” however, so solutions that are proven to be _better_ will take precedence over those that are _more compliant_. MVC just defines the *default* shape and thinking method.

!!!abstract "This idea is relatively new"
    Sokora was a poorly structured bot up until very short ago. Most of this “structuring“ is a new idea, so it is **not applied everywhere it could**. We’re gradually making things better and more consistent.

## How this is actually structured

The structure is well organized via the file system.

```ts
├── src
│   ├── api         // this is Interkora
│   ├── commands    // these are all bot commands, subdirs are command categories 
│   ├── containers  // reusable embeds
│   ├── database    // database files, settings module, and anything thats close to SQL; and a few types
│   ├── events      // each file is an event handler here (+ easter eggs are here too, in a subdir)
│   ├── features    // features, see features page to learn more
│   ├── handlers    // a few core very important files
│   ├── types       // all(most) data types
│   └── utils       // many useful things :D
└── tests           // test suite!
```

Omitted directories, if any, are not too relevant.

With all this in mind, you can serve yourself with the left sidebar for more pages. For simple contributions you can skip “The codebase“ and head to “Guidelines“. Read it all to get enough knowledge to do more complex stuff.

Also, thank you very much for passing by and thinking of contributing!

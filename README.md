Gradle Kotlin Js Bundler Plugin
===============================

A gradle plugin can extract required js files from dependent jars, and combine them with the js file generated by `compileKotlin2Js`, in correct order.

Please note that all the files generated by `compileKotlin2Js`(including dependencies) should use `plain` format type (which is default)

Publish
-------

Can only install to maven local for now:

```
./gradlew install
```

Use it
------

```
buildscript {
    repositories {
        mavenLocal()
    }
    dependencies {
        classpath 'freewind.github.com:gradle-kotlin-js-bundler-plugin:0.1.0'
    }
}

apply plugin: 'kotlin-js-bundler'

kotlinJsBundler {
    additionalJsFiles = []
    outputFile = "$projectDir/bundle.js"
}
```

Testing
-------

```
cd testing-project
./gradlew kotlinJsBundler
```

It will generate a `bundle.js` file when everything is working well, the file combined all required files like `kotlin.js`, so we can just include only one js file in `index.html`.

Then open `testing-project/index.html` and you will see

- an alert: `{"name":"Freewind"}`
- console: `my hello`, from external `my.js`

which means everything is OK.


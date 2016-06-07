# grublish
Absolutely minimal Bintray publishing via Gradle.

## Introduction
We have done our best to create an easy path to publishing with minimal _esoterica_. We accomplished this by replacing some of the more advanced/redundant settings with sensible defaults, and hiding the ugliness of maven archiving. We also assume that you will enter metadata like _license_ and _description_ using the UI at https://bintray.com

Creating a bintray account is outside the scope of this README, but it's really quite simple!

#### local.properties (or ~/.gradle/gradle.properties)
```gradle
bintray.user={your_bintray_username}
bintray.apikey={your_bintray_api_key} // you can find this at https://bintray.com/profile/edit
```

#### gradle.properties
```gradle
// the following EXAMPLE would be imported as:
// compile 'com.levelmoney:klarity:0.2'

publish.group = com.levelmoney

// THIS ABSOLUTELY MUST MATCH YOUR ANDROID STUDIO MODULE NAME BECAUSE OF REASONS. 
// WE APOLOGIZE FOR THIS.
publish.artifact = klarity

publish.version = 0.2

// publish.org = levelmoney // org is only needed if you're pushing to a team.
```

#### build.gradle
```gradle
buildscript {
  ...
  dependencies {
    ...
    classpath 'com.github.dcendents:android-maven-gradle-plugin:1.3'
    classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.6'
  }
}
```

#### {modulename}/build.gradle
```gradle
...
apply from: 'https://raw.githubusercontent.com/Levelmoney/grublish/master/gradle/module.gradle'
```

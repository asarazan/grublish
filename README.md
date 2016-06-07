# grublish
Absolutely minimal Bintray publishing via Gradle.

### Usage

#### Root build.gradle
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

#### Module build.gradle (append)
```gradle
apply from: 'https://raw.githubusercontent.com/Levelmoney/grublish/master/gradle/module.gradle'
```

#### gradle.properties
```gradle
// the following would be imported as:
// compile 'com.levelmoney:klarity:0.2'

publish.group = com.levelmoney
publish.artifact = klarity
publish.version = 0.2
// publish.org = levelmoney // org is only needed if you're pushing to a team.
```

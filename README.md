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
```properties
// publish.org = levelmoney // org is only needed if you're pushing to a team.
publish.group = com.levelmoney
publish.artifact = klarity
publish.version = 0.2
```
I've used [Klarity](https://github.com/Levelmoney/klarity) as an example. A user of your library would then import it as `compile 'com.levelmoney:klarity:0.2'`

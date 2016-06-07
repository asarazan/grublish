# grublish
Absolutely minimal Bintray publishing via Gradle.

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

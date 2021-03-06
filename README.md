In an ideal world, publishing to Bintray would be as easy as pulling from it.

We're not there yet, but we have done our best to create an easy path to publishing with minimal _esoterica_. We accomplished this by replacing some of the more advanced/redundant settings with sensible defaults, and hiding the ugliness of maven archiving. We also assume that you will enter metadata like _license_ and _description_ using the UI at https://bintray.com

### Before you begin
1. Sign up and create your package at https://bintray.com
2. **Make sure** your library module in Android Studio matches the name of your artifact. This is critical.
3. Cry for a bit.
4. Compose yourself and then check out the [Sample Project](https://github.com/Levelmoney/grublish/tree/master/grublish-sample).

#### local.properties (or ~/.gradle/gradle.properties)
```bash
grublish.user={your_bintray_username}

# you can find this at https://bintray.com/profile/edit
grublish.apikey={your_bintray_api_key} 
```

#### gradle.properties
```bash
# the following example would be imported as:
# compile 'com.levelmoney:klarity:0.2'

grublish.group = com.levelmoney
grublish.artifact = klarity
grublish.version = 0.2
# grublish.publish = true // by default, you have to go to bintray and manually hit publish
# grublish.org = levelmoney // org is only needed if you're pushing to a team.
```

#### build.gradle
```gradle
buildscript {
  ...
  dependencies {
    ...
    classpath 'com.github.dcendents:android-maven-gradle-plugin:1.4.1' // Android ONLY
    classpath 'com.jfrog.bintray.gradle:gradle-bintray-plugin:1.6'
  }
}
```

#### {modulename}/build.gradle
```gradle
...
apply from: 'https://raw.githubusercontent.com/Levelmoney/grublish/1.0.2/gradle/module-android.gradle' // Android Project
// OR
apply from: 'https://raw.githubusercontent.com/Levelmoney/grublish/1.0.2/gradle/module-java.gradle' // Java Project
```

#### Finally!
`./gradlew build install bintrayUpload`

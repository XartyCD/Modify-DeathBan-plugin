Изменить только build.gradle на:

plugins {
    id 'java'
}

repositories {
    mavenCentral()
    maven {
        url 'https://hub.spigotmc.org/nexus/content/groups/public/'
    }
    maven {
        url 'http://repo.extendedclip.com/content/repositories/placeholderapi/'
        allowInsecureProtocol = true
    }
    mavenLocal()
}

dependencies {
    compileOnly 'org.projectlombok:lombok:1.18.24'
    annotationProcessor 'org.projectlombok:lombok:1.18.24'
    testImplementation 'junit:junit:4.12' 
    compileOnly 'org.spigotmc:spigot-api:1.18.2-R0.1-SNAPSHOT' // Добавим зависимость Spigot API
    compileOnly 'com.google.code.gson:gson:2.8.9' // Добавим зависимость GSON 
    compileOnly 'me.clip:placeholderapi:2.9.2'
}

compileJava {
    options.compilerArgs += [
        '--add-opens', 'jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED',
        '--add-opens', 'jdk.compiler/com.sun.tools.javac.api=ALL-UNNAMED'
    ]
}

java {
    toolchain {
        languageVersion = JavaLanguageVersion.of(17) // Используем более стабильную версию JDK
    }
}




Компиляция в .jar через gradle 8.8:

1) gradle clean

2) gradle build  
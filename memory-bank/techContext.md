# Technical Context

## Operating System
- OS: Windows 10.0.19045
- Path Separator: \
- CLI: PowerShell (C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe)

## Development Environment
- IDE: Cursor AI IDE
- Workspace Path: F:\Program Files\Tubular
- Android Extension: adelphes.android-dev-ext

## Project Technical Stack
- Language: Java/Kotlin
- JDK Version: JDK 17 (F:\Program Files (x86)\jdk-17)
- Build System: Gradle 8.9
- Gradle Version: 8.7.1
- Kotlin Version: 1.9.25
- Compile SDK: 34
- Min SDK: 21
- Target SDK: 33
- Package/Namespace: org.schabi.newpipe (inherited from original NewPipe project)
- Application ID:
  - Release: org.polymorphicshade.tubular
  - Debug: org.polymorphicshade.tubular.debug
- Launch Command: 
  - ADB: `adb shell am start -n org.polymorphicshade.tubular.debug/org.schabi.newpipe.MainActivity`
  - VS Code: Need both packageName and activityName in launch.json

## Device Information
- Physical Device: Yes
- Device ID: 0I73C18I24101774
- API Level: 34

## Key Dependencies
- AndroidX Libraries
- ExoPlayer: 2.18.7
- OkHttp: 4.12.0
- Room: 2.6.1
- RxJava: 3.1.8
- ACRA: 5.11.3 (Crash reporting)
- Jsoup: 1.17.2 (HTML parsing)
- Picasso: 2.8 (Image loading)
- TubularExtractor (custom fork of NewPipeExtractor)

## Build Issues
- Unit test failures in `ImportExportManagerTest.kt` and `ImportAllCombinationsTest.kt`
- Missing resources like `db_ser_json.zip`
- Mockito `UnfinishedStubbingException` issues
- Current workaround: Building with `.\gradlew build -x test`

## Development Goals
- ✅ Fix: Device launch with correct package/namespace format
- Fix: USB disconnection issues
- ✅ Fix: Debugger "waiting for debugger" issue
- Features to implement: SponsorBlock and ReturnYouTubeDislike enhancements

## Known Issues
- Project location in Program Files may cause permission issues
- ADB connection stability problems
- Missing debug output
- Package name structure:
  - Internal namespace: `org.schabi.newpipe` (for Java/Kotlin code)
  - Application IDs: `org.polymorphicshade.tubular` & `org.polymorphicshade.tubular.debug` 
  - Launch syntax: `[applicationId]/[namespace].[ActivityName]`
  - Example: `org.polymorphicshade.tubular.debug/org.schabi.newpipe.MainActivity` 
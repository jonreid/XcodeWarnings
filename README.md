![XcodeWarnings](https://qualitycoding.org/wp-content/uploads/2021/06/XcodeWarnings-small1.png)

XcodeWarnings.xcconfig is an Xcode configuration file that lists all warnings and static analyzer
settings present in Xcode 15. Comment out any settings that won't help your project.

Accompanying blog post: [Xcode Warnings: Turn Them Up to Eleven!](https://qualitycoding.org/xcode-warnings/)

All warnings are enabled, with these exceptions:

**Commented Out by Default**

- "Pedantic Warnings" (`GCC_WARN_PEDANTIC`) isn't enabled because ordinary interaction with Apple's
  libraries makes it unhappy.
- "Treat Warnings as Errors" (`GCC_TREAT_WARNINGS_AS_ERRORS` and `SWIFT_TREAT_WARNINGS_AS_ERRORS`) aren't enabled because when
  experimenting with code, I sometimes temporarily comment out a line which uses a variable — which
  triggers the "Unused Variables" warning.
- "Unused Parameters" (`GCC_WARN_UNUSED_PARAMETER`) isn't enabled because it's not unusual to
  provide a method required by Apple's frameworks that ignores a parameter.

**Not Even Included**

- "Implicit Synthesized Properties" (`CLANG_WARN_OBJC_MISSING_PROPERTY_SYNTHESIS`) isn't included
  because in all likelihood, you don't need to be backwards compatible with non-modern Objective-C.
- "Disable Safety Checks" (`SWIFT_DISABLE_SAFETY_CHECKS`) isn't included in order to keep runtime safety checks when optimizing.
- "Inhibit All Warnings" (Apple Clang) and "Suppress Warnings" (Swift) aren't included because they're the opposite of our goals for this configuration.

## Static Analyzer

The Static Analyzer is also completely enabled, including "Deep" analysis during the Build action.
If that's too slow, comment out `CLANG_STATIC_ANALYZER_MODE` to restore faster "Shallow" analysis.

## Author

Jon Reid is the author of _[iOS Unit Testing by Example](https://iosunittestingbyexample.com)._ His website is [Quality Coding](https://qualitycoding.org).

[![Mastodon Follow](https://img.shields.io/mastodon/follow/109765011064804734?domain=https%3A%2F%2Fiosdev.space
)](https://iosdev.space/@qcoding)

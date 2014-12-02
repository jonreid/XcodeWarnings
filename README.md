Xcode Warnings
==============

Warnings.xcconfig is an Xcode configuration file that lists all warnings and static analyzer
settings present in Xcode 6.

Comment out any settings that won't help your project. In particular, Warnings.xcconfig enables
"Treat Warnings as Errors" (GCC_TREAT_WARNINGS_AS_ERRORS), which may be impractical for existing
projects.

All warnings are enabled, with these exceptions:

- "Pedantic Warnings" (GCC_WARN_PEDANTIC) isn't even included, because ordinary interaction with
  Apple's libraries makes it unhappy.
- "Unused Parameters" (GCC_WARN_UNUSED_PARAMETER) is disabled, because it's not unusual to provide a
  method required by Apple's frameworks that ignores a parameter.
- "Implicit Synthesized Properties" (CLANG_WARN_OBJC_MISSING_PROPERTY_SYNTHESIS) is disabled because
  modern Objective-C should avoid explicit @synthesize when possible.

The Static Analyzer is also completely enabled, including "Deep" analysis during the Build action.
If that's too slow, comment out CLANG_STATIC_ANALYZER_MODE to restore faster "Shallow" analysis.

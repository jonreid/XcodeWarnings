Xcode Warnings
==============

Warnings.xcconfig is an Xcode configuration file that lists all warnings and static analyzer
settings present in Xcode 6.

Comment out any settings that won't help your project. In particular, Warnings.xcconfig enables
"Treat Warnings as Errors" (GCC_TREAT_WARNINGS_AS_ERRORS), which may be impractical for existing
projects.

All warnings are enabled, with these exceptions:

*Disabled by Default*

- "Unused Parameters" (GCC_WARN_UNUSED_PARAMETER) is disabled, because it's not unusual to provide a
  method required by Apple's frameworks that ignores a parameter.

*Not Even Included*

- "Pedantic Warnings" (GCC_WARN_PEDANTIC) isn't included because ordinary interaction with Apple's
  libraries makes it unhappy.
- "Implicit Synthesized Properties" (CLANG_WARN_OBJC_MISSING_PROPERTY_SYNTHESIS) isn't included
  because in all likelihood, you don't need to be backwards compatible with non-modern Objective-C.

Static Analyzer
---------------

The Static Analyzer is also completely enabled, including "Deep" analysis during the Build action.
If that's too slow, comment out CLANG_STATIC_ANALYZER_MODE to restore faster "Shallow" analysis.

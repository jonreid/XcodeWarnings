![XcodeWarnings](http://qualitycoding.org/jrwp/wp-content/uploads/2016/01/XcodeWarnings.png)

XcodeWarnings.xcconfig is an Xcode configuration file that lists all warnings and static analyzer
settings present in Xcode 7. Comment out any settings that won't help your project.

All warnings are enabled, with these exceptions:

**Commented Out by Default**

- "Treat Warnings as Errors" (`GCC_TREAT_WARNINGS_AS_ERRORS`) isn't enabled because when
  experimenting with code, I sometimes temporarily comment out a line which uses a variable — which
  triggers the "Unused Variables" warning.
- "Unused Parameters" (`GCC_WARN_UNUSED_PARAMETER`) isn't enabled because it's not unusual to
  provide a method required by Apple's frameworks that ignores a parameter.
- "Multiple Definition Types for Selector" (`GCC_WARN_MULTIPLE_DEFINITION_TYPES_FOR_SELECTOR`) isn't
  enabled because it's not unusual to have a `@selector` on its own, apart from a method definition.

**Not Even Included**

- "Pedantic Warnings" (`GCC_WARN_PEDANTIC`) isn't included because ordinary interaction with Apple's
  libraries makes it unhappy.
- "Implicit Synthesized Properties" (`CLANG_WARN_OBJC_MISSING_PROPERTY_SYNTHESIS`) isn't included
  because in all likelihood, you don't need to be backwards compatible with non-modern Objective-C.

Static Analyzer
---------------

The Static Analyzer is also completely enabled, including "Deep" analysis during the Build action.
If that's too slow, comment out `CLANG_STATIC_ANALYZER_MODE` to restore faster "Shallow" analysis.

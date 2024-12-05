I am trying to disable all warnings for cmake target and I get the following warning:
>cl : command line  warning D9025: overriding '/W1' with '/w' [overriding_warning_level\.build\test_app_with_ignore_warnings.vcxproj]

In the case of the /W3 flag, there are no problems

In the case of the /w flag, some kind of /W1 appears, which I did not write anywhere
Everything is fine on the Ninja generator
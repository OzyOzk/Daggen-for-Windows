# Daggen-for-Windows
A basic port of Daggen for Windows machines

## Requirements

- Visual Studio 2019
- Build tools for Visual Studio 2019

## Compiling

You will need to add the pre-processor flag _CRT_SECURE_NO_WARNINGS to your project properties. See below for navigation.

`Properties>>C/C++>>Preporocessor>>Preprocessor Definitions>> _CRT_SECURE_NO_WARNINGS`

Make sure that you select "All Configurations" from the configuration option and x64 from the Platform option.

Compile in Release mode for x64 platforms.

## Warning

Daggen uses ctime and fopen. ctime takes a time_t reference as it's argument. For large values of time_t it can cause undefined behaviour. From the ctime description;

> This function returns a pointer to static data and is not thread-safe. In addition, it modifies the static tm object which may be shared with gmtime and localtime. POSIX marks this function obsolete and recommends strftime instead. The behavior may be undefined for the values of time_t that result in the string longer than 25 characters (e.g. year 10000)

fopen has been deprecated by Microsoft. Once you add _CRT_SECURE_NO_WARNINGS to your preprocessor definitions you should be fine.

## usage

Once compiled, daggen can be used by navigating your command window to where daggen.exe is located and carrying out the following command;

`daggen.exe daggen_test.exe -n 10 `

## Future Work

 - Replace ctime
 - Replace fopen

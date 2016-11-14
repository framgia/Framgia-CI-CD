# Violation comments to Github

Use this plugin for violation comments to GitHub

Image source: [framgiaci/violation-comments](https://hub.docker.com/r/framgiaci/violation-comments/). this using only for `build` section of the `.drone.yml`.

- Version 1.0
 * Violation support: AndoidLint, Checkstyle, CSSLint, Findbugs, Flake8, JSHint, PMD, ReSharper, XMLLint, CPPLint, Lint, CPPcheck, Perlcritic, Pitest.
 * Support only Github

# Environment:

 - `ENABLE` - true is enable, false is disable.
 - `COMMENT_ONLY_CHANGED_CONTENT` - Create one comment per violation.
 - `CREATE_SINGLE_FILE_COMMENTS` - Comment only changed part of files.
 - `CREATE_COMMENT_WITH_ALL_SINGLE_FILE_COMMENTS` - Create one big comment with all violations.
 - `VIOLATION_{FORMAT}` - (`Optional`) See example in below.

# Example

 The following is a sample configuration in your .drone.yml file:

 ```YML
 build:
   violationcomments:
     image: framgiaci/violation-comments
     environment:
       - ENABLE=true
       - CREATE_SINGLE_FILE_COMMENTS=true
       - CREATE_COMMENT_WITH_ALL_SINGLE_FILE_COMMENTS=false
       - COMMENT_ONLY_CHANGED_CONTENT=true
       - VIOLATION_CHECKSTYLE=.*/reports/checkstyle/.*\\.xml$
       - VIOLATION_CSSLINT=.*/reports/csslint/.*\\.xml$
       - VIOLATION_LINT=.*/reports/lint/.*\\.xml$
       - VIOLATION_FINDBUGS=.*/reports/findbugs/.*\\.xml$
       - VIOLATION_JSHINT=.*/reports/jshint/.*\\.xml$
       - VIOLATION_PMD=.*/reports/pmd/.*\\.xml$
       - VIOLATION_CPPCHECK=.*/reports/cppcheck/.*\\.xml$
       - VIOLATION_RESHARPER=.*/reports/reshaprper/.*\\.xml$
       - VIOLATION_FLAKE8=.*/reports/flake8/.*\\.xml$
       - VIOLATION_CPPLINT=.*/reports/cpplint/.*\\.xml$
       - VIOLATION_XMLLINT=.*/reports/xmllint/.*\\.xml$
       - VIOLATION_PERLCRITIC=.*/reports/perlcritic/.*\\.xml$
       - VIOLATION_PITEST=.*/reports/pitest/.*\\.xml$
       - VIOLATION_ANDROIDLINT=.*/reports/androidlint/.*\\.xml$
     commands:
       - violationcomments
 ```
The pattern may be, for example, `*/reports/checkstyle/.*\\.xml$` to match xml-files, in a folder named checkstyle, anywhere in workspace. You try [Regulex](https://jex.im/regulex/) for creating your regexp.



###### For only checkstyle:

 ```YML
 build:
   violationcomments:
     image: framgiaci/violation-comments
     environment:
       - ENABLE=true
       - CREATE_SINGLE_FILE_COMMENTS=true
       - CREATE_COMMENT_WITH_ALL_SINGLE_FILE_COMMENTS=false
       - COMMENT_ONLY_CHANGED_CONTENT=true
       - VIOLATION_CHECKSTYLE=.*/reports/checkstyle/.*\\.xml$
     commands:
     - violationcomments
 ```

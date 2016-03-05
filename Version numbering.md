Releases and version numbering policy
======================================

Summary
--------
- Lomse follows a version numbering scheme based on [semantic versioning](http://semver.org/).

- But the PATCH number is changed not only due to bug fixes but to any other backwards compatible change in the library not affecting the API, such as refactoring some code or any change in the repository not affecting the code.

- The lomse master repo is keept always buildable and usable. Do not wait for an official release. **The master repo contains always the latest release!**

**Important**: Please note that until Lomse has not reached version 1.0.0 these guidelines will not be followed. MINOR will be always changed when backwards incompatible changes in the API. But could also be changed due to a substancial change in architecture, API or other important changes.


Releases
-----------

- The lomse master repo is keept always buildable and usable. You can use the latest repo image without having to wait for an official release.

- Version information (MAJOR.MINOR.PATCH numbers) are **always updated after a merge**.

- An 'Official Release' is just a point in time in which it is decided to tag the repo and to create binary packages. Oficial  releases are done only:
    - if MAJOR or MINOR numbers change, or
    - from time to time, when a significant accumulated number of changes since previous release.

- Do not wait for an official release. The master repo contains always the latest release!


Numbering scheme
------------------

It is very important to define a stable API for users of the Lomse library. However, there will be always a need to improve the library and to keep it technologically updated. To balance these two needs, a strict policy of versioning is required, which users can rely upon to understand the limitations, restrictions, and the changes that can occur from one release of Lomse to the next one.

Lomse follows a MAJOR.MINOR.PATCH numbering scheme, aiming at communicating how difficult will be to update an application using Lomse. This, in turn, tells about the level of compatibility between the two releases.

Package versions have the form ‘MAJOR.MINOR.PATCH’, and are updated by the following rules:

- If any interfaces have been removed or changed, increment MAJOR, and set MINOR and PATCH to 0.

- Else, if backwards compatible functionality is introduced to the public API (more interfaces added) of if any public API functionality is marked as deprecated, then increment MINOR, and set PATCH to 0.

- Otherwise, change PATCH number.

**Important**:  The PATCH number is not incremented by 1 but incremented based on the number of commits since last release. Therefore, it could change in big steps from one release to the next one (i.e.: from 1.15.3 to 1.15.45).


Understanding the implications
--------------------------------

- A change in the MAJOR version must be interpreted as a milestone, normally due to a substancial change in architecture, API or other major changes, such as licensing. It must be assumed source and binary incompatibility with previous versions, althought this might not be true. Therefore, assume incompatibility and read release documentation.

- A change in the MINOR version number implies more functionality, features or significant fixes. Source code compatibility will be mostly preserved. That is, source code incompatibilities if any, will be minimal and limited to issues easy to fix in your code without reviewing the logic. I will not give guaranties about binary compatibility, althought it should be preserved unless you are using the library in not expected ways.

- Finally, changes in the PATCH level should be perfectly compatible, source and binary. It will include only bug fixes, refactoring code or changes not affecting the code.



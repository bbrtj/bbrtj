# Contributing to my Perl CPAN modules

Most of my modules are Dist::Zilla based, which eases much of the development but requires extra setup.
- First, install Dist::Zilla from CPAN with `cpanm Dist::Zilla`
- Second, install any Dist::Zilla dependencies of a given project: `dzil authordeps --missing | cpanm` (in the project root)
- Third, install any runtime dependencies: `dzil listdeps --missing | cpanm` (in the project root)
- You should be ready to run and build the project

_Side note: installing the built project does not require these steps. These are only required if you want to build from source. 
You can have a single perl with dzil setup and use it to build packages, and then you can test them with any other perl._

Dist::Zilla documentation can be found [on its website](https://dzil.org/index.html). You usually should need just a couple commands:
- `dzil build` builds the dist into a new subdirectory and packs it into `.tar.gz`
- `dzil clean` cleans the directory
- `dzil test` builds and tests the dist (it also executes author-only tests)
- `dzil release` builds and releases project to CPAN as well as tagging the current commit

Releasing a new version requires adding an entry in the `Changelog` file and increasing the version in `dist.ini`. 
I usually do these in a separate commit which will then get tagged by `dzil release`.

## Other tools

### Editorconfig

Your editor should read and obey rules present in `.editorconfig` file, if it is present in the project.

### Perl::Tidy and Code::TidyAll

Most of my projects use Perl::Tidy to adjust some parts of the syntax. It is best run with `tidyall -a`. 
You first need to run this command: `cpanm Perl::Tidy Code::TidyAll`. It is not run automatically, so you should run it by hand.

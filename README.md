*Werc* theme/port for *Hugo*
============================
This theme is a "port" of the website ("anti-")framework [werc][] for the
[Hugo][] static site generator.

[werc]: http://werc.cat-v.org/
[Hugo]: https://gohugo.io/

Rationale
---------
I like many aspects of *werc*'s UI/UX design. However, there are reasons
that I (and others) will use *Hugo* (or some other static site
generator) instead:
- *werc* is less "portable" for the following reasons:
  - It runs as a [CGI script][] on the webserver. Therefore, the user
    must have webserver-level access. Nowadays, many use something like
    [GitHub Pages][], [GitLab Pages][], or [Netlify][] to host their
    website free of charge; these services offer no such access.
  - It requires [Plan 9 utilities][], so the user's webserver must
    either already have those or allow them to be installed.
- *Hugo* has a lot of functionality (or bloat, depending on your
  interpretation) that *werc* doesn't.

[CGI script]: https://en.wikipedia.org/wiki/Common_Gateway_Interface
[GitLab Pages]: https://about.gitlab.com/stages-devops-lifecycle/pages/
[GitHub Pages]: https://pages.github.com/
[Netlify]: https://www.netlify.com/
[Plan 9 utilities]: https://tools.suckless.org/9base/

Design
------
This is intended to mimick *werc* as closely as possible, with minimal
user-specific changes. Hugo-izing changes are made so that the theme
works as expected with the [HugoBasicExample][] and passes the
`buildThemeSite.sh` test suite from the [hugoThemes][] repository.

[HugoBasicExample]: https://github.com/gohugoio/HugoBasicExample
[hugoThemes]: https://github.com/gohugoio/hugoThemes/

In the future, patch files may be added to `/patches/` for optionally
toggling certain user preferences. Users are welcome and encouraged to
submit such patches for inclusion in the repository. See
https://suckless.org/hacking/ for more information about patches and
patching.

The theme is built with `/updater.sh`, a [POSIX][]-compliant [Unix][] *sh*ell
script, to allow for reproducible builds. It takes in an arbitrary
*werc* source tree as input and outputs a corresponding *Hugo* theme. It
is designed for and tested with changeset 700 of *werc*'s
[official Mercurial repository][]. Using other versions may not work as
intended or cause errors. As of this writing, subsequent changes in the
upstream code have not affected the script's output, which is what we
are interested in.

[POSIX]: https://en.wikipedia.org/wiki/POSIX
[Unix]: https://www.howtogeek.com/182649/htg-explains-what-is-unix/
[official Mercurial repository]: https://code.9front.org/hg/werc

Status/Contributing
-------------------
The development of this project is incomplete. Users are encouraged to
submit pull requests with changes, particularly in the following areas:
- [ ] clean up src/updater.sh, switch from using *sed* to using
      *diff*/*patch*
- [ ] fix the sidebar to display the contents of the current page's
      parent directory and display double arrows on the current file
      (see *werc*).
- [ ] write/add documentation and screenshots

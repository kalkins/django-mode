# Django mode for Emacs

## How to install

1. Install [yasnippet](http://code.google.com/p/yasnippet/)
2. Add something like this to your Emacs config:

```lisp
(require 'django-html-mode)
(require 'django-mode)
(yas/load-directory "path-to/django-mode/snippets")
(add-to-list 'auto-mode-alist '("\\.djhtml$" . django-html-mode))
```

## Jumping
Move your cursor to a line that contains the thing you want to go and press `C-x j`.
Django-mode supports jumping to:

- templates, eg. `render_to_response('some.html')` will open some.html. (it supports `@render_to` from [annoying](http://bitbucket.org/offline/django-annoying), classic `render_to_response` and the new 1.3 `TemplateResponse`)
- views (from urls.py), urls.py and views.py must be in the same directory (no global urls.py for all apps, it's a bad practice after all!)
- models, from `Model.objects.*` or `Model(*)`, no support for `get_object_or_404(Model*` yet

## Inserting translation marks
Select a string you want to translate and press `C-t`. This works in both Python and templates.

## Running management commands
Check out the Django menu :)
BTW, default keybindings:

- `C-c m` asks for a command to run (with completion of all available commands and ido completion)
- `C-c t` runs tests
- `C-c s` runs syncdb
- `C-c a` creates an app (asking for a name first)

## Running a make target
With `M-x django-make` (`C-c M` in django-mode), you get a helm menu to choose a Makefile target. It will run from the project root (we use [helm-make](https://github.com/abo-abo/helm-make)).

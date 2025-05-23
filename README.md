# Post Processor Workbench

ppwb is a set of tools used in post-processing, the final stage of ebook
production.

The workbench is a web front-end written in PHP that performs a variety
of post-processing activities by calling out to external programs.
It consists of a user-visible page (`index.php`) with links to programs for
text analysis (see `pptext.php`), HTML analysis (see `pphtml.php`),
"smart quote" processing (see `ppsmq.php`) and a file compare tool
(see `ppcomp.php`).

The following two external tools need to be installed in directories under
`bin/`:
* [pptext](https://github.com/DistributedProofreaders/pptext) in `bin/pptext/`
* [pphtml](https://github.com/DistributedProofreaders/pphtml) in `bin/pphtml/`
* [ppcomp](https://github.com/DistributedProofreaders/ppcomp) in `bin/ppcomp/`

It's recommended that you clone those repos into `bin/` directly:

```bash
cd bin
git clone https://github.com/DistributedProofreaders/pptext.git
git clone https://github.com/DistributedProofreaders/pphtml.git
git clone https://github.com/DistributedProofreaders/ppcomp.git
```

See the individual tools' README.md for their prerequisites.

For ppcomp to work, `dwdiff` needs to be installed as well.

## Python environment

The external python programs require various python libraries to be installed
in order to work. Consult with each of the tools' `requirements.txt` files
for more details. These can be installed in the system's python3 installation
(not recommended) or in a virtualenv dedicated for ppwb (preferred).

If using a virtualenv, you need to update `$python_runner` in `config.php` to
call it like this:
```php
$python_runner = "env VIRTUAL_ENV=/path/to/venv PATH=/path/to/venv/bin/python3";
```

Ensure that the web server can access the virtualenv. virtualenvs created
in `~/.local` may need to have the permissions updated (o+x) to allow the
web server sufficient permissions.

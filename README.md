# Offensive Security Exam Documentation Repo

This repo offers a structure for Offensive Security exam documentation. Each machine
separated into it's own directory with individual scans, artifacts, and exploits
directories. Reports for individual machines are created in their individual `README.md`
files. When you have completed all machines, you can head to `report` and run `make` to
build a final PDF output and use `7zip` to produce the required files.

You will need to modify `front-matter.md` to modify the title page as well as `Makefile`
to modify your OSID.

When writing your individual machine documentation, any images should be placed in the
individual machine directory under `img`. These are symlinked to `report/img` during
building, so they shouldn't conflict with names of other machine images. Consider adding
a prefix.

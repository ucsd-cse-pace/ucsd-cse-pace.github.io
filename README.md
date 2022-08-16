# pace.ucsd.edu website

This repository:

- Stores logos for PACE
- Stores HTML/CSS/images for the PACE website
- Automatically deploys to https://ucsd-cse-pace.github.io/ when you commit and push to it
- Can be *manually* deployed to pace.ucsd.edu by using Actions -> Deploy to pace.ucsd.edu -> Run Workflow (from main branch)

## Editing

You can edit the HTML/CSS/images directly through the Github editing interfaces.
When you commit/save, you will be able to see your changes reflected in https://ucsd-cse-pace.github.io/ a few minutes later.
It's also fine to clone and edit locally and push later, but for quick updates the web interface on Github is particularly convenient,
especially if the goal is to just fix up some typos, etc.

The site is completely built in HTML and CSS, and there is no build system – it's just the files you see.
As more pages get added it may be worth adding a build system to share a common header, etc.
The Bootstrap CSS library is directly copied/hosted in the repository, which is the main exernal dependency for layout.

The most relevant documentation is [Bootstrap's grid system](https://getbootstrap.com/docs/4.0/layout/grid/).
The CSS in `pace.css` is written to take advantage of this, and the media queries around specific widths like `720px` and `1440px` are designed
around the breakpoints Bootstrap has defined for "small", "medium", "large" screens.

## Deploying

The script in `.github/workflows` is responsible for copying the files to pace.ucsd.edu when we trigger the action.
It has a SSH key for the `pace` user stored as a [repository secret](https://docs.github.com/en/actions/security-guides/encrypted-secrets), and uses `scp`
to copy and overwrite all the files in the relevant target directory on that host.

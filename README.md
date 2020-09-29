# 数据赋能 智能互联 Workshop

### Setup:

#### On a Mac:
Install Hugo:
`brew install hugo`

#### On Linux:
  - Download from the releases page: https://github.com/gohugoio/hugo/releases/tag/v0.64.1
  - Extract and save the executable to `/usr/local/bin`

#### Clone this repo:
From wherever you checkout repos:
`git clone https://github.com/Kervin-AWS/workshop-auto-iot.git` (or your fork)

#### Clone the theme submodule:
`cd workshop-auto-iot`

`git submodule init` ;
`git submodule update`

#### Install Node.js and npm:
You can follow instructions from npm website: https://www.npmjs.com/get-npm

#### Install node packages:
`npm install`

#### Run Hugo locally:
`npm run server`
or
`npm run drafts` to see stubbed in draft pages.

`npm run build` will build your content locally and output to `./public/`

`npm run test` will test the built content for bad links

#### View Hugo locally:
Visit http://localhost:8080/ to see the site.

#### Making Edits:
As you save edits to a page, the site will live-reload to show your changes.

#### Auto Deploy:
Any commits to main will auto build and deploy in a couple of minutes. You can see the currently
deployed hash at the bottom of the menu panel.


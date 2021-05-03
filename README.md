# FIND YOUR HOUSE API

<p align="center">
  <img src="./source/images/logo.png" alt="API Documentation" width="226">
  <br>
</p>

> This project started as a fork of the popular [Slate](https://github.com/tripit/slate) API documentation tool, which uses ruby.

Welcome to the FIND YOUR HOUSE API! You can use our API to access FIND YOUR HOUSE API endpoints, which can get information on various houses in our database.

The FIND YOUR HOUSE API is organized around REST. Our API has predictable resource-oriented URLs, accepts form-encoded request bodies, returns JSON-encoded responses, and uses standard HTTP response codes, authentication, and verbs.

We have language bindings in Ruby, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

<img src="./source/images/Screenshot.png" alt="Screenshot" style="margin: auto; display: block">

## API AND DOCUMENTATION LINKS

[API Documentation](http://gbisimwa.me/Find-house-api-doc/)
[API Live Demo Link](https://find-your-house-backend.herokuapp.com/)

## Dependencies

Minimally, you will need the following:

- [Ruby](https://www.ruby-lang.org/en/) >= 2.5
- [Bundler](https://bundler.io/)
- [NodeJS](https://nodejs.org/en/)
- [Git](https://git-scm.com/)

Please note, only Linux and macOS are officially supported at this time. While slate should work on Windows, it is unsupported.

See below for installation instructions for different OSes / distros.

### Installing Dependencies on Linux

Install Ruby, NodeJS, and tools for compiling native ruby gems:

**On Ubuntu 18.04+**

```bash
sudo apt install ruby ruby-dev build-essential libffi-dev zlib1g-dev liblzma-dev nodejs patch
```

**On Fedora 31+**

```bash
sudo dnf install @development-tools redhat-rpm-config ruby ruby-devel libffi-devel zlib-devel xz-devel patch nodejs
```

Then, update RubyGems and install bundler:

```bash
sudo gem update --system
sudo gem install bundler
```

### Installing Dependencies on macOS

First, install [homebrew](https://brew.sh/), then install xcode command line tools:

```bash
xcode-select --install
```

Agree to the Xcode license:

```bash
sudo xcodebuild -license
```

Install nodejs runtime:

```bash
brew install node
```

Update RubyGems and install bundler:

```bash
gem update --system
gem install bundler
```

## Getting Set Up

1. Fork this repository on Github.
2. Clone _your forked repository_ (not our original one) to your hard drive with `git clone https://github.com/YOURUSERNAME/slate.git`
3. `cd slate`
4. Install ruby gems for slate:

```shell
# either run this to run locally
bundle install
```

Note: if the above fails on installing nokogiri and using macOS see
[here](https://github.com/sparklemotion/nokogiri.org/blob/master/docs/tutorials/installing_nokogiri.md#macos)
for some helpful tips on things that might help.

## Running slate

You can run slate in two ways, either as a server process for development, or just build html files.

To do the first option, run:

```bash
bundle exec middleman server
```

and you should see your docs at http://localhost:4567. Whoa! That was fast!

The second option (building html files), run:

```bash
bundle exec middleman build
```

## What Now?

The next step is to [learn how to edit `source/index.md` to change the content of your docs](Markdown-Syntax). Once you're done, you might want to think about [deploying your docs](https://github.com/slatedocs/slate/wiki/Deploying-Slate).

## Companies Using Slate

- [NASA](https://api.nasa.gov)
- [Sony](http://developers.cimediacloud.com)
- [Best Buy](https://bestbuyapis.github.io/api-documentation/)
- [Travis-CI](https://docs.travis-ci.com/api/)

You can view more in [the list on the wiki](https://github.com/slatedocs/slate/wiki/Slate-in-the-Wild).

## Questions? Need Help? Found a bug?

If you've got questions about setup, deploying, special feature implementation in your fork, or just want to chat with the developer, please feel free to [start a thread in our Discussions tab](https://github.com/slatedocs/slate/discussions)!

Found a bug with upstream Slate? Go ahead and [submit an issue](https://github.com/slatedocs/slate/issues). And, of course, feel free to submit pull requests with bug fixes or changes to the `dev` branch.

## Contributors

Slate was built by [Robert Lord](https://lord.io) while at [TripIt](https://www.tripit.com/). The project is now maintained by [Matthew Peveler](https://github.com/MasterOdin) and [Mike Ralphson](https://github.com/MikeRalphson).

FIND YOUR HOUSE API was built by :

👤 **Guillain Bisimwa**

- Github : [@guillainbisimwa](https://github.com/guillainbisimwa)
- Twitter : [@gullain_bisimwa](https://twitter.com/gullain_bisimwa)
- Linkedin : [guillain-bisimwa](https://www.linkedin.com/in/guillain-bisimwa-8a8b7a7b/)

## Show your support

Give a ⭐️ if you like this project!

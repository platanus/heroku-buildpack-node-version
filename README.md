# Heroku Buildpack Node Version

This buildpack will read the node version from the project's `.node-version` file and inject that version into the `package.json` as a value for the `engines.node` key. This way the node binaries installations are delegated to the **heroku-buildpack-node**.

It also revolve node versions to the (if applies) semver range. For example:

```shell
#.node-version
10.16
```

The buildpack will inject a semver range into the `package.json`.

```shell
# Buildpack output
-----> Getting Node version from .node-version file
-----> Found Node version: 10.16
-----> Adding Node version to package.json: 10.16.x
```

## Usage

Use this buildpack with [heroku-buildpack-node](https://github.com/heroku/herok-buildpack-node) using buildpack layering with [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi).

Point the buildpack to ddollar's [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi):

    $ heroku buildpacks:set https://github.com/ddollar/heroku-buildpack-multi.git

Add this repository to your `.buildpacks` file:

    https://github.com/platanus/heroku-buildpack-node-version.git
    https://github.com/heroku/heroku-buildpack-node.git

## Requirements

This buildpack `detect` scripts checks the following:

- The presence of a `.node-version`
- The presence of a `package.json`

## Credits

Thank you [contributors](https://github.com/platanus/heroku-buildpack-node-version/graphs/contributors)!

<img src="http://platan.us/gravatar_with_text.png" alt="Platanus" width="250"/>

heroku-buildpack-node-version is maintained by [platanus](http://platan.us).

## License

Potassium is © 2016 platanus, spa. It is free software and may be redistributed under the terms specified in the LICENSE file.

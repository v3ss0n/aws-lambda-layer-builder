# Pylayerize
Pylayerize simplifies the process of creating AWS Lambda Layers by leveraging Docker to compile and package Python dependencies for any targeted runtime. With support for custom packages and private GitHub repos, pylayerize optimizes the creation and deployment of Lambda Layers for improved development efficiency.

### General Usage
To use Pylayerize, you must first install it using pip:
```ruby
$ pip install pylayerize
```
Once pylayerize is installed, you can run it from the command line by invoking the pylayerize command.
```ruby
$ pylayerize -tp <target_package> [OPTIONS]
```

#### Required Options:

-tp, --target-package: The target package to build a layer for.

#### Optional Options:

-h, --help: Show the help message and exit.
-op, --output-path: The output path for the layer .zip file. Default is the current directory (.).
-n, --output-layer-name: The name of the output .zip file. Default is lambda_layer.
-ll, --log-level: The log level of logging. Default is INFO.
-gu, --git-username: The git username to use for the git clone.
-gp, --git-password: The git password to use for the git clone.
-rt, --runtime: The runtime to use for the layer. Default is python3.8.
--console-log, --no-console-log: Log to console. Default is True.
--local, --no-local: Set to True if you want to use a requirments.txt file or a custom lib stored locally. Default is False.

#### Examples
To build a layer for numpy using the default options, run:

```ruby
$ pylayerize -tp my_package
```

To build a layer for numpy with a custom output path and layer name, run:

```ruby
$ pylayerize -tp numpy -op /path/to/output -n my_layer
```

To build a layer for private GitHub repositories that require authentication, run:
```ruby
$ pylayerize --target-package git+my_repo_link --git-username my_username --git-password my_password
```

If you have a local requirements.txt file at /path/to/requirements.txt, you can use it by running

```ruby
$ pylayerize --target-package mypackage --local --requirements-file /path/to/requirements.txt
```

#### Programatic Usage

It is also possible to use pylayerize and its components programatically in Python.

```python
from pylayerize import build_aws_lamda_layer
```


### Contributions

Contributions are welcome! Here are some guidelines for contributing to this project:

Fork this repository and create a new branch for your feature or bug fix.
Make your changes and commit them with descriptive commit messages.
Create a pull request against the dev branch and describe your changes and the problem they solve.
Ensure that your code passes all tests and meets the project's code standards.
Respond to any feedback from maintainers and make any necessary changes.
If you'd like to contribute but aren't sure where to start, take a look at the project's issue tracker. Issues marked as "help wanted" or "good first issue" are a good place to start.
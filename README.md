Title: A powerful and structured CFEngine framework

# A powerful and structured CFEngine framework

[CFEngine 3](http://www.cfengine.com) is a powerful configuration management tool that's speed, small footprint, multi-platform support, network resilience and agent-based approach attract many.

However, many have a hard time with the language and tooling, and need an easier way. CFEngine has been [described](https://digitalelf.net/2013/04/a-case-study-in-cfengine-layout/) as flour, eggs, milk and butter. All the ingredients needed to make a cake, but no recipe. __ncf__ is that missing recipe, and much more.

ncf is a framework that runs in __pure CFEngine__, to help __structure__ your CFEngine policy and provide __reusable, single purpose components__ distributed under the __GPLv3__ license.

## Philosophy

ncf is designed with the following concepts at all times:

  - __DRY__: You should never have to duplicate promises, or even promise patterns. This is the best way to make unmaintanable code.
  - __KISS__: Keep everything Simple and Sweet :) This extends to having one bundle do one thing, but do it well. Avoid complexity.
  - __Minimal effort__: Reduce typing and syntax effort for everyday use as much as possible. Make the framework do the heavy lifting - code once, benefit forever! (aka "Lazy" :) )
  - __Intuitive__: Reading and writing configuration management rules with ncf should be self-evident. Clearly named bundles and conventions make this easy.
  - __Extensible__: You should be able to extend anything, add methods or support for new tools easily, without breaking anything.

## Decoupled layers

There are several layers in this framework, from 10 to 60, with each layer being a foundation for higher levels. The higher the lever, the higher the abstraction level.

  - __10_ncf_internals__: This directory contains the mechanics and glue to make the framework work. This should be very rarely modified, and is generic.
  - __20_cfe_basics__: This directory contains libraries that can be reused; most notably the CFEngine Standard Library.
  - __30_generic_methods__: This directory contains reusable bundles, that perform unit tasks, and are completely generic (for example "file_create_symlink"). All generic methods are documented on http://www.ncf-project.org/pages/reference.html.
  - __40_it_ops_knowledge__: This directory contains default values for services, like package names for a specific service accross diferent distributions (aka "is it httpd or apache2?"), paths to binaries, default configuration values for services, etc.
  - __50_techniques__: This directory contains Techniques, which combine generic_methods and it_ops_knowledge to acheive system configurations you need. They may be generic ("Configure OpenSSH server") or specific ("Install and configure our in-house app").
  - __60_services__: This directory contains high-level service definitions, by calling individual techniques, with parameters and conditions. This level is specific for each organisation, and is intended to define services such as "Corporate web site" rather than "Apache config".

Each level uses items from lower levels (lower numbers) or, in some cases, from its own level.

## Requirements

There are none, other than CFEngine itself.

Some tooling is provided (ncf CLI), but it is not mandatory. It is designed to help developing your policy. The tooling is all in Python, and required Python 2.6+.

# Documentation Philosophy

Here's how I like to organize technical documentation for a software product/service. The core idea is to organize docs so it's easy to find what you need, across many use-cases, like:

- newcomer needs orientation to the product/service -- what's it for? How to install it?
- user needs help with a specific error they encountered while using it.
- maintainer needs a short list of steps to deploy a new version of the service.
- etc.

This was inspired by the "Diataxis" framework, see [the official site](https://diataxis.fr/) or [this conference video](https://www.youtube.com/watch?v=t4vKPhjcMZg).


## Summary

Here's my organization method:

- 2 sets of docs: one for "users" of the product/service, one for "maintainers" who build/deploy/host the product/service.
- for each audience (user / maintainer), docs organized into 4 categories:
	- quick start - minimal working example for a newcomer to the platform. Step-by-step instructions w/ brief explanations. Goal: get something working, show the value, and introduce the user to key concepts.
	- use cases - showcase what it's good for, once you know what you're doing. beginner, intermediate, advanced.
	- how-to - step-by-step "recipes" for common uses & troubleshooting.
	- explanations - longer essays for deeper discussion of important concepts, design decisions, architecture.

```text
- user					# asdf
	- quick-start.md	# asdf
	- use-cases.md		# asdf
	- how-to/			# asdf
- maintainer			# asdf
	- quick-start.md	# asdf
	- how-to/			# asdf
	- explanations/		# asdf
```

- Note: maintainers need to know everything a user knows, and more. So it's natural for the maintainer docs to link back to the user docs. But user docs shouldn't point to the maintainer docs, because users shouldn't have to know anything about the "guts" of the service.


## Example

A developer productivity team at a web-development tech company offers a command-line tool named "Deven" for other internal software engineers to run common development tasks, like:

- open a Rails console for customer X's live deployment
- open a database viewer for the QA deployment of app Y
- download the codebase for (internal) service Z, install it, and start its local dev server on localhost

The Deven tool comes pre-installed on engineers' company laptops. Deven's users are software engineers with general technical knowledge.

Moreover, Deven supports a plugin system, whereby engineers can write domain-specific plugins for Deven to extend its functionality. For example, the technical documentation team wrote a plugin to make it easier for engineers to generate docs for their apps and import those docs into the company's Developer Portal. For simplicity, the docs for plugins are included under the "maintainers" documentation (not the Users docs).

The docs are structured like this:

- user
	- quick-start.md
		- what the tool does, how it can help you
		- installation steps
		- most common commands
		- next steps for learning more
	- use-cases.md
		- (If Deven was more of a "platform" or framework, rather than a simple CLI tool, this section would list some impressive & useful ways it has been used, to inspire users to take the time to adopt it.)
	- how-to/
		- how to open a customer's backup database in the TablePlus DB viewer
		- how to open a Rails console on a deployed QA site
		- how to ssh into a QA site
		- how to generate a boilerplate code for a new "Browely" test (our internal browser-automation testing framework)
		- how to add your project's docs to the Dev Portal
		- how to generate a Architecture Decision Record template in your repo's docs
		- how to update the Deven tool and its plugins
		- how to list installed Deven plugins
		- how to write a Deven plugin
		- how to troubleshoot common Deven errors
		- how to view Deven logs
- maintainer
	- quick-start.md
		- read the user's quick-start to understand what Deven is
		- install the Deven development environment and run the dev version locally
	- how-to/
		- how to deploy a new version of Deven
		- how to add a new feature to Deven
		- how to run Deven's tests
		- how to audit / approve a plugin submitted by another dev team
		- how to add / edit / delete members of the Deven development group
		- how to troubleshoot common errors during Deven development
	- explanations/
		- Deven system architecture
			- authentication
			- permissions
		- Deven plugins
			- architecture: Deven-to-Plugin interface
			- lifecycle of a Deven plugin
			- plugin style guide
		- architecture decision records
			- 2024-06-06 - ADR 01 - change logging library from Log4J to Loggr
			- 2024-08-11 - ADR 02 - update CLI library - migration to Ocaml


I hope this helps you structure your docs in a useful way!!

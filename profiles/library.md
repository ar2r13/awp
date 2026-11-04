# Library

Create a library module only when a reusable package is actually needed. Do not
extract shared code or add a package registry as a bootstrap convention.

In local module instructions, capture the public API location, supported runtime,
consumers, compatibility constraints, and verified check/build commands when known.
Keep publishing and versioning decisions explicit; bootstrap does not authorize
package publication.

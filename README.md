# Ducker (Limbo)

This is a port of ducker from Plan9 C to Inferno Limbo.

Ducker provides (by default) non-negotiable namespace sandboxing.

In particular, ducker aims to better automate the process of sandboxing arbitrary processes. 

## Build

	mk

## Usage

- You cannot use a proto and an arch file at the same time
- You must supply either a cfg or a command argument
- You cannot use `-g` to generate an ns file while not providing an proto/arch file

	ducker [-Dg] [-p proto | -a arch] [-n namespace] [-r root] [-c cfg] [-u user] [cmd args…]

### Examples

Touch(1) a file in the current directory:

	ducker `{whatis touch} `{pwd}^/test

Run a web server with a proto as the fs template, generating our namespace file:

	ducker -g -p web.proto -c web.cfg /dis/svc/httpd/httpd

Run a web server with an archive as the fs template and web.ns for the namespace:

	ducker -d web.arch -c web.cfg -n web.ns /dis/svc/httpd/httpd

Run touch(1) in /tmp:

	ducker -p examples/tmp.proto -c examples/tmp.cfg

## References

- [ducker](https://github.com/henesy/ducker)
- [sys-pctl(2)](http://man.cat-v.org/inferno/2/sys-pctl)
- [mkfs(8)](http://man.cat-v.org/inferno/8/mkfs)
- [archfs(4)](http://man.cat-v.org/inferno/4/archfs)
- [proto(6)](http://man.cat-v.org/inferno/6/proto)
- [namespace(6)](http://man.cat-v.org/inferno/6/namespace)
- [9front's newns(8)](http://man.cat-v.org/9front/8/auth)

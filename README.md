## Issue description

If `rules_proto` init is placed before `rules_docker` in WORKSPACE file, there will be error on docker build: 

```bash
bazel build --platforms=@build_bazel_rules_nodejs//toolchains/node:linux_amd64 //src:docker

Starting local Bazel server and connecting to it...
ERROR: /private/var/tmp/_bazel_sib/7e0a4dda28e20d87e5bba3cee1c0c969/external/io_bazel_rules_go/go/tools/coverdata/BUILD.bazel:3:1: in go_tool_library rule @io_bazel_rules_go//go/tools/coverdata:coverdata:
Traceback (most recent call last):
	File "/private/var/tmp/_bazel_sib/7e0a4dda28e20d87e5bba3cee1c0c969/external/io_bazel_rules_go/go/tools/coverdata/BUILD.bazel", line 3
		go_tool_library(name = 'coverdata')
	File "/private/var/tmp/_bazel_sib/7e0a4dda28e20d87e5bba3cee1c0c969/external/io_bazel_rules_go/go/private/rules/library.bzl", line 42, in _go_library_impl
		go.archive(go, source)
	File "/private/var/tmp/_bazel_sib/7e0a4dda28e20d87e5bba3cee1c0c969/external/io_bazel_rules_go/go/private/actions/archive.bzl", line 219, in go.archive
		sets.union(cgo_exports, *[a.cgo_exports for a...])
	File "/private/var/tmp/_bazel_sib/7e0a4dda28e20d87e5bba3cee1c0c969/external/bazel_skylib/lib/new_sets.bzl", line 184, in sets.union
		struct(_values = dicts.add(*[s._values ...]))
	File "/private/var/tmp/_bazel_sib/7e0a4dda28e20d87e5bba3cee1c0c969/external/bazel_skylib/lib/new_sets.bzl", line 184, in struct
		dicts.add(*[s._values for s in args])
	File "/private/var/tmp/_bazel_sib/7e0a4dda28e20d87e5bba3cee1c0c969/external/bazel_skylib/lib/new_sets.bzl", line 184, in dicts.add
		s._values
object of type 'list' has no field '_values'
ERROR: Analysis of target '//src:docker' failed; build aborted: Analysis of target '@io_bazel_rules_go//go/tools/coverdata:coverdata' failed; build aborted
```

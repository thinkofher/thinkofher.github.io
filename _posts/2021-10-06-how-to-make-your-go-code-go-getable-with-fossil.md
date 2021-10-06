---
title: "How to make your Go code go-getable with fossil (or other non-git vcs)?"
author: thinkofher
website: "https://github.com/thinkofher"
tags: go dev fossil
layout: post
---

The post below is a copy from a wiki page from [hauru.club/x/example](//code.hauru.club/example)
repository. It stores sample golang package hosted with fossil [VCS](//en.wikipedia.org/wiki/Version_control). I've
had created it to show people how to manage golang packages with fossil VCS and be able to
download them with `go get` tool.

### Prerequisites

* Your own internet domain. They are very cheap today, especially if you choose some obscure [tld](https://en.wikipedia.org/wiki/Top-level_domain) like `*.club` or `*.xyz`.
* Some VPS. You can use this referral [link](https://www.vultr.com/?ref=8942073-8H) to gain some free credits during registration at [vultr](https://vultr.com).
* Go compiler, some text editor, cool project name etc.

### VPS

I won't give you detailed instructions on how to setup your own domain and
VPS, because it is not in the scope of this document and folks smarter than
me had prepared good materials regarding [setup and maintenance](https://landchad.net/)
of VPSes.

#### Github pages

If you don't want to manage your own web server you can just use
[github pages](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
with your domain. But you still need some place to self-host fossil
anyway<strong>*</strong>.

### Fossil server

Follow actual [fossil documentation](https://fossil-scm.org/home/doc/trunk/www/server/debian/nginx.md),
it consists a lot of practical examples and answers most questions. Remember that
you can use `--repolist` flag of `fossil server` subcommand to
[serve](https://fossil-scm.org/home/doc/trunk/www/server/any/none.md) multiple fossil
repositories.

### Meta tag

You should add special page with the same directory path as the desirable go import
path. For example: if you want your import path to be `example.com/x/package` you
should create file `package.html` in the `x` directory in the root of your web server.
Your `package.html` document has to contain special `<meta>` tag in the head node.
According to [go documentation](https://pkg.go.dev/cmd/go#hdr-Remote_import_paths), the
`meta` tag has the form:

```html
<meta name="go-import" content="import-prefix vcs repo-root">
```
Example `meta` tag for `example.com/x/package` import path and source code located
at `https://fossil.example.com/package` managed by fossil VCS could looks like:

```html
<meta name="go-import" content="example.com/x/package fossil https://fossil.example.com/package">
```

You can add more pages for other go projects with the corresponding meta tag.

### Testing

If everything is properly setup you should be able to download your source code for
project with valid `go.mod` file by typing `go get example.com/x/package` command in
your terminal window. You can also check if the documentation for your project is
available at the [godocs.io](https://godocs.io) or [pkg.go.dev](https://pkg.go.dev).

### Conclusion

Having your own custom go import path isn't really a thing. Nothing stops you from
using the knowledge and experience from this tutorial to make your project go-getable
with vcs other than the fossil. You may also want to setup custom go import paths for
your projects hosted at github.

If you want to share some thoughts after reading this post, feel free to contact [me](/contact).


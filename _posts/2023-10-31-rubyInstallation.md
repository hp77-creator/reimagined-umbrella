---
layout: post
title: "Installing Ruby in MacOS"
date: 2023-10-31
---

## Ruby

If you are reading this, I am assuming this that you know that a 
language like Ruby exists. It is little bit like Python but is a
lot different. Ruby on Rails is one of the most frameworks to create
web applications. For more information you can look up on Google.

## Why Ruby in MacOS?

So, I thought of installing Ruby because I really want to write blogs.
I looked up various places where I can write blogs and Jekyll stood out of all of them.
Jekyll is a static-site-generator tool written in Ruby and Thanks to [this](https://github.com/skills/github-pages)
beautiful guide by Github that I was able to set it up instantly.

But I wanted to do local development and check out my deployed pages in local first
before posting them onto my portfolio repo. Jekyll is written in Ruby and hence I had to
install Ruby. [Here](https://jekyllrb.com/docs/) is the guide that I followed.

:warning: Read [Requirements](https://jekyllrb.com/docs/installation/#requirements) and [Pre-Requisites](https://jekyllrb.com/docs/installation/) tab before proceeding to install Jekyll.

## Things to keep in mind while installing Ruby on MacOS

### While installing another version of ruby from `ruby-install`

If you are from :india: India, there is a possibility that your ISP might not allow you
to install `ruby` from `ruby-install`. Reason is that few ISPs in India block `raw.githubusercontent.com`.
I learnt about this the hard way, I had to try the same command in different systems to know such a problem existed.
To resolve this problem, You can add a DNS server in your wifi/network. [Here](https://stackoverflow.com/a/76757237/7116645) is one way.

### During installation of another version of ruby from `ruby-install`

It might happen that you see the following error:

```shell
ossl_ts.c:829:5: error: incomplete definition of type 'struct TS_verify_ctx'
    TS_VERIFY_CTX_set_certs(ctx, x509inter);
    ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// ...
make[1]: *** [ext/openssl/all] Error 2
make: *** [build-ext] Error 2
+__rvm_make:0> return 2
1 warning and 1 error generated.
```

To resolve this run the following command before `ruby-install ruby 3.1.3`:
```shell
export CONFIGURE_ARGS=""
for ext in openssl readline libyaml zlib; do 
  CONFIGURE_ARGS="${CONFIGURE_ARGS} --with-$ext-dir=$(brew --prefix $ext)" 
done
```